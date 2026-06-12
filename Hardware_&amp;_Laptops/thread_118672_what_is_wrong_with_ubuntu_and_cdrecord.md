---
title: "what is wrong with ubuntu and cdrecord?"
date: 2006-01-17
forum: Hardware &amp; Laptops
---

### Post by hca on 2006-01-17
I have serious problems writing cd's in ubuntu using cdrecord.
Using any other distro i can do a cdrecord -scanbus and get:
Cdrecord-Clone 2.01a19 (i686-pc-linux-gnu) Copyright (C) 1995-2003 J\uffffrg Schilling
Using libscg version 'schily-0.7'
scsibus0:
0,0,0 0) ' ATAPI ' '48X CDROM ' '3.40' Removable CD-ROM
0,1,0 1) 'LITE-ON ' 'DVDRW SOHW-1693S' 'KS09' Removable CD-ROM
0,2,0 2) *
0,3,0 3) *
0,4,0 4) *
0,5,0 5) *
0,6,0 6) *
0,7,0 7) *
hca@compaq5686:~$


but using ubuntu I get :
hca@compaq5686:~$ cdrecord -scanbus
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
and thus may have bugs that are not present in the original version.
Please send bug reports and support requests to <cdrtools@packages.debian.org>.
The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.12-10-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
hca@compaq5686:~$

would somebody PLEASE tell mi what do I do wring, OR what is bad with ubuntu

---

### Post by mpvano on 2006-01-17
The problem is not so much with ubuntu as it is with cdrecord. It's author is, as you can see, extremely hostile to the idea of modifying it to work with the changes made in going to kernel 2.6 - the current linux kernels.

Despite the messages he's built in to it, and the other tools he built. It seems to work fine. The problem is that to install it, the ubuntu team had to make a modification he apparently does NOT approve of - hence the nasty messages.

If the following command doesn't work directly with your drive:

cdrecord -checkdrive

(which should report information about your drive) try this one:

cdrecord dev=/dev/hdc -checkdrive

(or substitute for /dev/hdc, the actual device name of your drive).

If this works but the first command didn't you need to configure the file /etc/default/cdrecord properly. (or just always include dev=/dev/hdc in all your cdrecord commands).

If this doesn't work, make sure you are part of the "cdrom" group using the "Users and Groups" tool in the system menu. You must be part of this group (or use the sudo command) to burn cds. In some cases, you ALWAYS need to use the sudo command to burn certain types of CDs, however. Try it if you can't get anything else to work.

If none of these is your problem, your drive may not be installed correctly, or may not be supported for some reason. If your drive is not an ide or atapi drive, there could be problems with the USB, firewire, or scsi interface or drivers for it.

Try reading all the documentation in  /usr/share/doc/cdrecord/README.ATAPI.setup.ubuntu (which contains the above information and more).

Despite the scary message cdrecord generally works just fine - ignore it! The author (who we all owe a lot to for doing much of the groundwork that allows cd burning on linux and other platforms today) is just "venting". Many of the issues he's complaining about are valid, but don't need to stop you from using the software....

hope this helps,

Mario

---

### Post by hca on 2006-01-19
thank you SO MUCH. This was just what I needed in order to get going!

---

### Post by Enginerd on 2006-01-19
I am having a similar problem... i have done like you listed above but got the same bad result for both. Something about error trying to open dev. I can attach if that helps.  i am fairly new to Linux let alone Ubuntu. 

One thing that i did notice is that if i do sudo i can burn. So i made sure i was in the cdrom group, yep im there. 

So could the problem lie in being a AD domain user? Am i stuck sudoing to burn cds or logout to a local user account?

Any help would be appreciated.

Enginerd

---

### Post by mpvano on 2006-01-19
You may have a problem with the permissions for the device or one of the libraries  of cdrecord on your system, but If I were you, I'd just use sudo - it's not that big a deal is it, and there's usually no security risk if you only use it for duration of the one command?

I'm not sure I know what an "AD domain" user is. I've never seen that term before under any flavor of unix and I have no comprehension about what you are saying about having to logout to a local user account - what is a "local user" account - how are you trying ot use the system? If you're not a normal user then I'm not surprised your having authentication problems.

If you're trying to say that you're not the first account created on the machine, and so have no sudo rights from your account, then your administrator should be able to fix that for you.

Also, are you really using Dapper Drake? If so, I have no idea what your problems could be - that's beta software distributed so you can help find bugs.

Also, why are you using cdrecord at all? It doesn't have that much to recommend it over serpentine and the nautilus builtin burner. I occasionally use cdrdao to make disks with more exotic features, but cdrecord is usually a last resort for me. I never use it unless I can't make anything else work.

Sorry I can't be more help.....

Mario

---

### Post by Enginerd on 2006-01-20
No you have been a lot of help. I am fairly new to linux in general but i have always been daring with learning by jumping in, so yes i am using dapper. However i am having the same problem so i dont think it is a dapper issue. However it may be a AD (permission) issue.

As far as your question about AD domain user. All that means is that i have the system setup to Authenticate against an active directory domain server. Win2k3. So i am not the Local(machine) user.

As far as permissions i have sudo privliges and am also the admin so i have no problem using  sudo. It just feels like a cheap hack to do something that i could do in breezy testing.

So basiclly im just trying to learn why and help fix it but it is by no means a show stopper.

Enginerd

---

### Post by Cysman on 2006-01-23
I'm having the exact problem also.  I'm completely new with linux.  How do I put myself into the user group?  You'll have to draw it out in crayon for me I'm afraid.  I am noticing that when I check the properties of my cdrw, it tells me that I'm not the owner and permissions to burn are not selected for any user.

---

### Post by Enginerd on 2006-01-23
Open a terminal window (CLI)

~$ sudo adduser yourusername cdrom

that should do it.

You should be able to burn if you use sudo then your record command. If you are using gnomebaker or a graphical use gksudo. 

Im a bit of a newb myself so i hope this helps. If not imsure some one more experienced than I will be along to help.

Enginerd

---

### Post by jstaple on 2006-10-09
Try this...

1. Add yourself (Your user account) to the disk group (System->Administration->Users and Groups)
2. Goto System->Preferences->Removable Drives and Media and untick everything in the storage tab
3. Try and burn a CD again

You will have to put these ticks back when you want automount to work again.

This worked for me. Don't treat as a difintive answer give it a try and see if it works for you.

---

