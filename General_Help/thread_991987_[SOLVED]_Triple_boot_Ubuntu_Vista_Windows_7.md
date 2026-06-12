---
title: "[SOLVED] Triple boot Ubuntu Vista Windows 7"
date: 2008-11-24
forum: General Help
---

### Post by Mgiacchetti on 2008-11-24
OK.  
Here's my setup.

Grub with entries for ubuntu and vista(loader)

Vista loader runs a seperate grub for special purposes, then returns the vista boot selection with 
Vista
Windows 7


Basically (for reasons i will not discuss) I need to move windows 7 from the vista boot menu to the first grub.

I have tried the manual approach of just adding it to the menu.list and it returns "bootmgr missing" error and tells me to restart with my dvd.  

I dont want to do it that way.  I just need to move some files over to the windows 7 partition.


C: Vista 
D: windows 7
E: Data
Ubuntu 
Swap

SO what files do i need to move/modify?

---

### Post by Mgiacchetti on 2008-11-24
Allright, i figured it out.

in the following, vista refers to the old install, win7 to the new install


1. download and install vistabootpro onto the win7 install
2. copy the following files from the vista drive to the win7 drive(you may need to uncheck the "hide protected operating system files" and choose "show all files" in the folder options dialog):
```

c:\bootmgr
the entire contents of c:\boot

```you will most likely experience an error copying c:\boot\bcd
you can ignore this error for now.


3. open an elevated command prompt (start menu > cmd > ctrl+alt+enter) and type 
```

bcdedit /export x:\boot\bcd

```where x is the win7 drive where you copied the c:\boot

now restart.

4. Enter Ubuntu, and add a new entry into your menu.list to correspond to your newly installed os.
(basically, copy the first vista entry, and change the partition/drive numbers, and the name so you can distinguish between the two)  

run Startup-Manager  (if you dont have it, open synaptic, in the search on the top, search for startup manager, install the first one in the list.)

choose your default boot os (whichever you fancy).
restart.

select win7 from the list.

5. once in win7, open vistabootpro   
you will probably be presented with a lot of errors about "registry not valid".  Just click ok. many times.

if not already there, navigate to the "backup and restore" portion of the program. 

Choose the restore button, and navigate to the vista c:\boot\bcd and click apply

you will now see a dialog confirming that it has been successful.

close vistabootpro.


6. Start menu > msconfig

on the boot tab, decrease the timeout for os selection. apply and restart.


7. Choose the new os (win7) again, to verify the timeout change there.

hit ESC

8. choose the other windows os (vista) and verify that the timeout has NOT changed here.

continue booting into this one, and when at the desktop.  start menu > msconfig
on the boot tab, 

remove the win7 entry from this list, and (if necessary) make this one (vista) default.  apply. restart

9. boot back into windows 7 and repeat the above steps to remove vista from the boot entry, and make win7 default.

apply restart.



Now, you should have grub taking care of all your booting needs.  when you select ubuntu, it should boot there,   if you select vista, it should go straight there, and if you select win7, it should go straight there..

Hope this helps others, as I have been unable to find a step by step like this for this type of problem.

---

