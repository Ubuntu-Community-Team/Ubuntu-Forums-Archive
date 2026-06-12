---
title: "running professional software packages compatible with windows"
date: 2008-08-04
forum: General Help
---

### Post by anuran on 2008-08-04
Dear Friends, 

I am new to linux. I am into civil engineering profession and I need to work on packages like AutoCad , Staad Pro , SAP . I installed the softwares using wine version 1.0 . They were installed perfectly but when double click on the icon of Staad Pro .. ubuntu diplays message 'starting Staad-Pro' and then it wont start up.. the program is terminated thereon. I have configured wine for windows xp. I'll b thankful for the solution. [:)]
treat assured!!:popcorn:

---

### Post by hal10000 on 2008-08-04
try to start the application from a terminal-window, so you can see the error-messages appearing.
[COLOR="Red"]wine ~/.wine/drive_c/Programs/staadpro.exe/[/COLOR]
(your path to the application may be another, this is only an example)
Post the output of the error messages.

---

### Post by Taxman415a on 2008-08-04
If they crash like that after you try to run them, then they probably just don't run that well in Wine, unfortunately. Wine isn't perfect, they have a lot of work to do to recreate undocumented windows interfaces, including bugs that many programs depend on. 

In any case, [http://appdb.winehq.org/](http://appdb.winehq.org/) is the place to search for how compatible a program is with Wine. There isn't even a listing for Staad Pro, so I'd be surprised if you could run it well. A search for Autocad found some versions run very well, some not so much, so it depends. SAP doesn't really have a listing either, so I'd be very surprised if it runs as well.

So basically if you need these programs a good option is to install windows in a virtual machine running on Ubuntu. Then you can run all these programs inside of that. You just need a decent system with a good amount of RAM. Virtualbox, VMware and KVM are some options to look into.

Here's a good link on Virtualbox. I have it running and it works very well.
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by anuran on 2008-08-04
This is the output i got when i ran the program from the terminal...

--------------------------------------------------------------------
anuran@anuran-laptop:~$  wine ~/.wine/drive_c/Spro2004/STAAD/Staadpro.exe
err:module:attach_process_dlls "dbSectionInterface.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Spro2004\\STAAD\\Staadpro.exe" failed, status c0000005
anuran@anuran-laptop:~$ 
-------------------------------------------------------------

I tried the virtualbox and completed upto the step of mounting image of windows xp as mentioned in the site. when i started the os, i got the following error message..

----------------------------------------------------------------------
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
-----------------------------------------------------------

thATS HOW IT LOOKED

[IMG]http://picasaweb.google.co.uk/anu.nt.here/Technothlon/photo#5230756481000619538[/IMG]

what's next?? :(

---

### Post by estyles on 2008-08-04
you probably need to do this:

```
sudo adduser $USER vboxusers
```

I believe that $USER is a macro that will automatically expand to your username, but you could also replace it with user:user, where user is your username.  You will need to logout for the change to take effect (according to your error message).

---

### Post by jocko on 2008-08-04
> **anuran said:**
> This is the output i got when i ran the program from the terminal...

--------------------------------------------------------------------
anuran@anuran-laptop:~$  wine ~/.wine/drive_c/Spro2004/STAAD/Staadpro.exe
err:module:attach_process_dlls "dbSectionInterface.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Spro2004\\STAAD\\Staadpro.exe" failed, status c0000005
anuran@anuran-laptop:~$ 
-------------------------------------------------------------

I tried the virtualbox and completed upto the step of mounting image of windows xp as mentioned in the site. when i started the os, i got the following error message..

----------------------------------------------------------------------
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
-----------------------------------------------------------

thATS HOW IT LOOKED

[IMG]http://picasaweb.google.co.uk/anu.nt.here/Technothlon/photo#5230756481000619538[/IMG]

what's next?? :(

To get virtualbox working, you first have to add your user to the group vboxusers:
```
sudo adduser [COLOR=Red]username[/COLOR] vboxusers
```Where [COLOR=Red]username[/COLOR] should be your username.
Then log out of gnome and log in again.

---

### Post by anuran on 2008-08-04
Did the adduser part previously too...did it again and it gave the following result

anuran@anuran-laptop:~$ sudo adduser anuran vboxusers
[sudo] password for anuran: 
The user `anuran' is already a member of `vboxusers'.
anuran@anuran-laptop:~$

---

### Post by anuran on 2008-08-05
thank you all friends, i have successfully used virtualbox for windows xp. :)... . as promised.. here is the treat to all :popcorn:... have your popcorn guys.. :P ..lol . 

thanks a lot guys.

---

### Post by sbnwl on 2011-09-01
Here is how I could make it run after a lot of google around. Thanks to [http://www.wine-reviews.net/wine-reviews/tips-n-tricks/odbc-databases-jet-access-success-with-wine-1126.html](http://www.wine-reviews.net/wine-reviews/tips-n-tricks/odbc-databases-jet-access-success-with-wine-1126.html)

First Install Jet Service Pack 4.0 and MDAC 2.8 by firing the following commands in a terminal:

winetricks jet40
winetricks mdac28

Then you need to import the "HKEY_LOCAL_MACHINE/ SOFTWARE /ODBC" registry key from a "Microsoft Windows XP" installation to your Wine PREFIX.

Use the following command to launch registry editor in wine:

wine regedit

And use the "Registry > Import Registry File" to import it.

Make sure you already made a backup of whole Wine registry before that import.

Launch Staad Pro, and Make Models, Analyze them and Post Process them so seamlessly at almost same speed as on Windows OS.

Enjoy! :guitar:

---

### Post by cariboo on 2011-09-01
Things have changed in the three years that have elapsed since this thread was started. Closed

---

