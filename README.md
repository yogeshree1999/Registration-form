# Registration-form
basic registration form required for basic purpose in any of era. Here the geometry is used for creating a page on tkinter window, entry is used for adding user given input values,label is used to specify what input to be taken from user,buttonis used for giving response to input values.checkbutton is used to select any of the one given option,drop down is used to choose any of the option listed.


from tkinter import *
import sqlite3
root=Tk()
root.geometry('500x500')
root.title("Registration Form")

Fullname=StringVar()
Email=StringVar()
var=IntVar()
c=StringVar()
var1=IntVar()

def database():
    name1=Fullname.get()
    email=Email.get()
    gender=var.get()
    country=c.get()
    prog=var1.get()
    conn=sqlite3.connect('Form.db')
    with conn:
        cursor=conn.cursor()
    cursor.execute('CREATE TABLE IF NOT EXISTS Student(Fullname TEXT,Email TEXT,Gender TEXT,country TEXT,Programming TEXT)')
    cursor.execute('INSERT INTO Student(FullName,Email,Gender,country,Programming)VALUES(?,?,?,?,?)',(name1,email,gender,country,prog,))
    conn.commit()

label0=Label(root,text="Registration Form",width=20,font=("bold",20))
label0.place(x=90,y=53)
label1=Label(root,text="Full Name",width=20,font=("bold",10))
label1.place(x=80,y=130)
entry1=Entry(root,textvar=Fullname)
entry1.place(x=240,y=130)
label2=Label(root,text="Email",width=20,font=("bold",10))
label2.place(x=68,y=180)
entry2=Entry(root,textvar=Email)
entry2.place(x=240,y=180)
label3=Label(root,text="Gender",width=20,font=("bold",10))
label3.place(x=70,y=230)
Radiobutton(root,text="Male",padx=5,variable=var,value=1).place(x=235,y=230)
Radiobutton(root,text="Female",padx=20,variable=var,value=2).place(x=290,y=230)
label4=Label(root,text="country",width=20,font=("bold",10))
label4.place(x=70,y=280)
list1=['India','Canada','UK','Nepal','South Africa']
droplist=OptionMenu(root,c,*list1)
droplist.config(width=15)
c.set('select your country')
droplist.place(x=240,y=280)
label5=Label(root,text="Programming",width=20,font=("bold",10))
label5.place(x=85,y=330)
var2=IntVar()
Checkbutton(root,text="java",variable=var1).place(x=235,y=330)
Checkbutton(root,text="python",variable=var2).place(x=290,y=330)
Button(root,text="Button",width=20,bg='brown',fg='white',command=database).place(x=180,y=380)
root.mainloop()





