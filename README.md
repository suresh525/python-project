# python-project
#Zip file extract to desire format with GUI using Tkinter
from tkinter import *
import os,zipfile
def conv():
	e3.delete(0,END)
	p=e1.get()
	path=os.path.split(p)
	os.chdir(path[0])
	zp=zipfile.ZipFile(path[1])
	zpinfo=zp.namelist()
	ext=e2.get()
	v=0
	for file in zpinfo:
		if file.endswith(ext):
			v+=1
			zp.extract(file)
			val='convert successfully'
			e3.insert(0,val)
	if v==0:
		val='convert fail'
		e3.insert(0,val)
win=Tk()
f1=Frame(win)
f1.pack()
f2=Frame(win)
f2.pack()
f3=Frame(win)
f3.pack()
l=Label(f1,text='ZIP CONVERTER',bg='yellow',fg='blue')
l.pack()
l1=Label(f2,text="enter your bath:",fg='blue')
l1.grid()
l2=Label(f2,text="(.txt,.xlsx,.csv,etc..,):",fg='blue')
l2.grid(row=1)
e1=Entry(f2)
e1.grid(row=0,column=1)
e2=Entry(f2)
e2.grid(row=1,column=1)
b=Button(f2,text="CONVERT",activebackground='red',command=conv)
b.grid(row=2,column=1)
l3=Label(f2,text='NOTIFICATION:',fg='red')
l3.grid(row=2,column=0)
e3=Entry(f2)
e3.grid(row=3,rowspan=3)

win.mainloop()
