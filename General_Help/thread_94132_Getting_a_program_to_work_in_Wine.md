---
title: "Getting a program to work in Wine"
date: 2005-11-23
forum: General Help
---

### Post by earth_walker on 2005-11-23
We use a couple of windows project management software packages at my work, all older (win95/98 era), but have capabilities that none of the linux alternatives (nor the less-then-10-grand windows alternatives) have. So in my efforts to free all of us here from windows, I'm trying to get one of them to work under Wine.

There were problems with the installer (the security form does not give enough spaces to type in the key) so I just copied the install from my windows partitions.

Basically when I try to run it, I'm getting a bunch of dll not found errors like this:
[INDENT]err:module:import_dll Library PRMALLOC.dll (which is needed by L"C:\\Program Files\\myprogram\\PRMCRT.dll") not found[/INDENT]
For about 10 dlls supplied by the software manufacturer. 

My hope was that since this is not a 'could not load' error,  it's just a matter of permissions or being in the correct path. However, all of these ddls are in the .wine/drive_c/windows/system directory, and I have set the owner of all the drive_c directories to myself. I have also tried copying the dlls to the program directory, but wine still complains of not finding the dlls.

Any ideas? Any suggestions as to where I can go for some usefull help on deciphering wine errors in general?

Thanks
EW

---

### Post by darknuala on 2005-11-23
Try going to [http://www.winehq.com](http://www.winehq.com)

What kind of project software are you trying to install?  Did you check to see if there was a viable linux alternative?

---

### Post by earth_walker on 2005-11-23
[QUOTE=darknuala]Try going to [http://www.winehq.com](http://www.winehq.com)

What kind of project software are you trying to install?  Did you check to see if there was a viable linux alternative?[/QUOTE]

Yes, I have spent lots of time reading winehq, franksplace and websearching. No help deciphering the error messages. Wine is working fine for notepad, winefile, winmine, etc. Dcom98 is installed.

As I mentioned above, none of the linux alternatives I've tried are viable - as in not compatible with our existing projects nor provide the resource optimisation routines we need - like MS Project they are pretty Gantt chart makers or simple time management apps.

I'm sure there are proffessional offerings out there, but we have already spent $$$ on this particular one, and I would like to try to get it running in wine.

Edit: The software I'm trying work with is Primavera P3. And no, it is not in the wine working software list

---

### Post by darknuala on 2005-11-23
Try using crossover office.  You can download a free trial.  It works with alot of windows software, that wine doesn't do as well.

---

### Post by earth_walker on 2005-11-23
Thanks, darknuala, I'll give that a try in the morning.

---

### Post by sjh on 2005-11-23
[QUOTE=earth_walker]


 However, all of these ddls are in the .wine/drive_c/windows/system directory


[/QUOTE]

Just incase this isn't a typo, try the dll's in the system32 directory.

SJH

---

