---
title: "Can't find usable init.tcl file"
date: 2008-08-04
forum: General Help
---

### Post by buchta1 on 2008-08-04
I am pretty new to ubuntu and linux in general.  I am trying to run a program I just downloaded and am getting the following error message.

The program is Gridgen version 15.  The company who produces it is pointwise.

Application initialization failed: Can't find a usable init.tcl in the following directories: 
    ../../../linux/lib/tcltk/lib/tcl8.3 ../../../linux/lib/tcltk/lib/tcl8.3



This probably means that Tcl wasn't installed properly.

I have read up on this problem and how it is looking for the init.tcl in the wrong place etc.  However, I have changed the the TCLLIBPATH in my .bashrc file to the correct path to the library and I still get this error message.

If anyone has any advice that would be great.

Thanks

---

### Post by lisati on 2008-08-04
Which program are you trying to use? Perhaps some other forum member has had similar troubles with the same program and found a solution.

---

### Post by buchta1 on 2008-08-04
the program is Gridgen version 15.  I think it is run by a company called pointwise.

---

### Post by kresten on 2008-08-23
Hi I have a similar problem with a scientific program I use. I have used the same program since the very first version of ubuntu(4.10?) without problems so I know the problem is related to ubuntu 8.04 or at least the way tcl is installed in 8.04. A possible solution could be to place a symbolic link in one of the directories in which you program searche for it(ln -s /path/to/init.tcl) my init.tcl is in /usr/share/tcltk/tcl8.4 or something like that.

---

### Post by bhargavigoswami on 2012-12-07
I faced the same problem during my last installation of ns2.35 in ubuntu 11.04.
After I install ns2.35, got message of successful installation of ns. Then I set path in /.bashrc. Then I gave ns command which gave me same error which you got. 

The problem is because, ns executable is also at /usr which is conflicting.

Solution: 
1. Go to location root-usr-local-bin by giving following command in terminal
cd /usr/local/bin
2. There you would find the ns file. We just need to remove it by giving following command
rm ns
3. Thats it, you are done. Now your ns starts running successfully.

Happy Learning.....

---

### Post by lisati on 2012-12-07
A lot can change in four years. Old thread closed.

---

