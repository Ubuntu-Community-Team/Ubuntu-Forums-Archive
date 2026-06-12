---
title: "Grub error"
date: 2008-09-09
forum: General Help
---

### Post by OSUfrk09 on 2008-09-09
When i go to boot up ubuntu i get this... [GRUB4Dos 0.4.3 2008-06-03, Memory :638k/510M, codeEnd:0x41A38 Minimal BASH-like line editing is supported| and it gives me a dos menu and doesn't allow me to boot into ubuntu. 

GRUB4Dos 0.4.3 2008-06-03, Memory :638k/510M, codeEnd:0x41A38 Minimal BASH-like line editing is supported

HELP.  

I do not want to reinstall, and when i type boot under the command line in GRUB... it tells me that the kernels need to be loaded before booting. 

I Did install under wubi, and everything has run fine until this point

---

### Post by numone007 on 2008-09-10
A judge asked our group of potential jurors whether anyone should be excused, and one man raised his hand."I can't hear out of my left ear," the man told the judge. "Can you hear out of your right ear?" the judge asked. The man nodded his head. "You'll be allowed to serve on the jury," the judge declared. "We only listen to one side of the case at a time."----------------------------------------------------------------Volt [power inverter](http://www.zonzen.com/power-inverter.html) portable ,power inverter make it, shop for power inverter,Equipment [power supply manufacturer](http://www.zonzen.com) , power supply manufacturer can be referenced, this power inverter is well, the [proximity switches](http://www.zonzen.com/sensor-industry-switchgear.html) simatic px offer you,A guide on [switching power supply](http://www.zonzen.com).The [vitiligo](http://www.cureforvitiligo.com) pamphlet vitiligo is a skin, an introduction to vitiligo by the vitiligo society.

---

### Post by jmib55 on 2008-09-11
+1
I installed Wubi to test Ubuntu on my XP Home based PC. I have the same problem (same CodeEnd, same Grub version)

---

### Post by caljohnsmith on 2008-09-11
Do either of you have a menu.lst in your C:\ubuntu\disks\boot\grub\ directory? I believe that is where it is supposed to be. If you don't have one, you'll need to create one, and I can help with that.

---

### Post by Madzola on 2008-09-11
I'm having the same problem.
I checked here C:\ubuntu\disks\boot\grub\ directory
and there was no menu.lst
Help?

---

### Post by caljohnsmith on 2008-09-11
> **Madzola said:**
> I'm having the same problem.
I checked here C:\ubuntu\disks\boot\grub\ directory
and there was no menu.lst
Help?
OK, boot your Live CD, open a terminal, and please post the output of the following:
```
sudo blkid
```
That will give us a place to start, and then we can try and create a menu.lst for you.

---

### Post by Madzola on 2008-09-11
I don't know what my live cd is.
I uninstalled ubuntu and accidentlly didn't backup the file so now wubi is downloading it again for me.
It might take a while.
D:

---

### Post by Madzola on 2008-09-12
K I reinstalled it how do I fix this.
D:

---

### Post by ago on 2008-09-12
Press insert rapidly at boot (after selecting "Ubuntu") for a more verbose output and post the error message. 

Also search this forum for "fstest"

---

### Post by jmib55 on 2008-09-12
I does not have any menu.lst in C:\ubuntu\disks\boot\grub\ directory - nor in C:, nor in G: (the external USB drive where Wubi installed Ubuntu). However, I found 2 menu.lst files in subdirectories G:\ubuntu\winboot and in G:\ubuntu\install\boot\grub

I do not have any Live CD. I downloaded Wubi from Internet then started it. But in my G:/ubuntu directoy, I see a iso file (ubuntu-8.04.1-desktop-i386.iso)

Here is my ubuntu directory
[FONT="Courier New"]
G:\ubuntu>dir
 Volume in drive G is EXTERNE 1
 Volume Serial Number is 6853-5BA9

 Directory of G:\ubuntu

11/09/2008  21:50    <DIR>          .
11/09/2008  21:50    <DIR>          ..
11/09/2008  21:50    <DIR>          disks
11/09/2008  21:50    <DIR>          docs
11/09/2008  21:50    <DIR>          install
11/09/2008  21:50    <DIR>          winboot
11/09/2008  21:50           113.936 Uninstall-Ubuntu.exe
08/07/2008  02:12            25.214 Ubuntu.ico
11/09/2008  22:16             3.712 metadl_log.txt
11/09/2008  22:16             2.588 curl_log.txt
               4 File(s)        145.450 bytes
               6 Dir(s)  389.601.099.776 bytes free

G:\ubuntu>[/FONT]

---

### Post by Madzola on 2008-09-12
I did the press insert thing but I don't think it did any good.
I'll post what it said anyway.
GRUB4DOS 0.4.3 2008-06-30 Memory: 638k/478m, CodeEnd:0x41A38
[Minimal BASH-like line editing is supported. For the first word, TAB
List possible command completions. Anywhere else tab lists the possible completions of a device/filename. ESC at any time exits]

grub>

---

### Post by jmib55 on 2008-09-12
use of fstest give "ntfs_mount: 0" for all test on C: and G: (inode, info, list)

---

### Post by jmib55 on 2008-09-12
> **ago said:**
> Press insert rapidly at boot (after selecting "Ubuntu") for a more verbose output and post the error message. 

Ok I did it ! I got

```
Booting GRLDR ...
```

then each time I press "insert", I got additional information:

```

hard_drives: 1, int13 ....
get_diskinfo(80) ....
boot_drive=80 ....
get_cdinfo(7F) ....
starting cmain ... Open/Default ... failure

end of menu init ....

```

The information are relatively long. which line do I need to completely post here ? Is there a kind of log file ?

---

### Post by Madzola on 2008-09-12
Yeah I am pretty much totally gonna give up.
My computer probably just doesn't work with linux.
I'm not computer smart enough to do what you guys tell me anyway.
](*,)

---

### Post by caljohnsmith on 2008-09-12
> **Madzola said:**
> Yeah I am pretty much totally gonna give up.
My computer probably just doesn't work with linux.
I'm not computer smart enough to do what you guys tell me anyway.
](*,)
I can totally understand your frustration; Linux has not evolved as far as Windows has in terms of doing everything from a GUI, nor does Linux have as much of the hardware driver support that Windows has. Not having all the hardware drivers though is not Linux's fault, because most of the hardware companies cater totally to Windows, and on top of that, of course all their drivers are closed-source. You might have an easier time if you just repartition your HDD and do a standard Ubuntu install. But any way you install Linux, you will probably have to learn at least some of the "under-the-hood" stuff to get Linux working 100% the way you want. These forums are a great resource that way if you are willing, but if you don't have the time or inclination, I can understand that too.

---

### Post by Madzola on 2008-09-12
I have the time to do it but I don't know if partitioning has a chance of killing my data, which I can't back up since I don't have a room on my external. I am not sure of my skills doing technical stuff so I don't really trust myself to do anything unless its simple or I have the help of someone that knows what they are doing.

---

### Post by jmib55 on 2008-09-13
I am testing the solution presented in 
[http://ubuntuforums.org/showthread.php?t=612072&referrerid=662451](http://ubuntuforums.org/showthread.php?t=612072&referrerid=662451)
Hope I will not crash my PC...

---

### Post by caljohnsmith on 2008-09-13
EDIT: Never mind what I posted here before, I need to check some things before I can offer any (hopefully useful) help.

---

### Post by schloss on 2008-09-14
> **caljohnsmith said:**
> 
Look in your C:/ubuntu/disks/boot/ directory, and if you have a different kernel and initrd then the above 2.6.20-16-generic, then change the above lines accordingly. Let me know how it goes.

I'm having issues with my own Wubi setup, and when I look in C:/ubuntu/disks/boot I see nothing there (other than the grub/ folder). I'm guessing that's a problem. How can I fix that?

---

### Post by jmib55 on 2008-09-14
> **jmib55 said:**
> Hope I will not crash my PC...

Did not crashed :) but did not solved the issue :(. 
I think I will stop here my trial to have a dual boot solution and keep Windows alone for a few more time.

However, thanks for your information and good luck to the others.

---

