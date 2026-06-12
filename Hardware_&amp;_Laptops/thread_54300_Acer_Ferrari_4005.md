---
title: "Acer Ferrari 4005"
date: 2005-08-04
forum: Hardware &amp; Laptops
---

### Post by Cosmic_Crusader on 2005-08-04
G'Day!

I bought a Acer Ferrari 4005 laptop and have been attempting to get the amd64 version of Ubuntu working. Not all is working so I am going to switch to 32bit soon (I'd like to use the laptop and not get stuck in endless tweak mode - I've got Gentoo on my server for that). :p

So I installed Hoary 5.04 and the xorg display didn't work on first boot. I could press Ctrl+Alt+F1 to get a console though so it wasn't a crash.

Switched to vesa driver in xorg.conf and got a working visual, but no touchpad.

To get the touchpad working all I had to do was:[indent]  rmmod psmouse ; modprobe -v psmouse
[/indent]I have also added Tamir's amd64 repository detailed at:[indent][indent][http://ubuntuforums.org/showthread.php?t=48905]("http://ubuntuforums.org/showthread.php?t=48905")
  [/indent][/indent]In doing so I upgraded the kernel to 2.6.12 which didn't appear to make any difference with matters.

I noticed a problem with the CPU appearing to be 100% used.[indent][indent][http://www.ubuntuforums.org/showthread.php?p=278589]("http://www.ubuntuforums.org/showthread.php?p=278589")
  [/indent][/indent]Things that don't currently work that I am focussing on:


[list]
[*]CPU scaling
[*]  3D graphics acceleration
[/list](I have not yet tried WLAN)

Although the biggest problem so far is I noticed the following every 30s in the system logs:
[indent] Aug  4 21:13:46 localhost kernel:     ACPI-0352: *** Error: Looking up [Z00I] in namespace, AE_NOT_FOUND
 Aug  4 21:13:46 localhost kernel: search_node ffff810002f3bf80 start_node ffff810002f3bf80 return_node 0000000000000000
Aug 4 21:13:46 localhost kernel: ACPI-1138: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff810002f34e40), AE_NOT_FOUND
[/indent]I believe the answer is available somewhere here:[indent][http://acpi.sourceforge.net/dsdt/index.php]("http://acpi.sourceforge.net/dsdt/index.php")
[/indent]Not sure how much longer I'll be trying to get it working perfectly, I am definitely looking forward to breezy though!!! \\:D/

Any helpful pointers will be muchly appreciated.

---

### Post by xkcdmagic8 on 2005-08-04
acpi support is hell, ive tried too much - ill be running more kernel compiles today to figure it out :)

X700 is pretty simple you just have to know your stuff see this post: [http://ubuntuforums.org/showthread.php?p=286593#post286593](http://ubuntuforums.org/showthread.php?p=286593#post286593) (ill get a better list of things to do in 3-4 hrs) 

I thought CPU scaling WAS working last time i installed ubuntu (Some days ago) - I had the applet up and i was watching it go form 800 - 2000 so i believe thats already working.

---

### Post by Cosmic_Crusader on 2005-08-04
[QUOTE=nitinshantharam]acpi support is hell, ive tried too much - ill be running more kernel compiles today to figure it out :)[/QUOTE] I've yet to delve too deeply into that so I'm interested to hear any progress you make. I think the aforementioned link ([http://acpi.sourceforge.net/dsdt/index.php]("http://acpi.sourceforge.net/dsdt/index.php")) might help in that area.  I read something about being able to generate an ACPI thingie (yup - gotta read up on that).

[QUOTE=nitinshantharam] X700 is pretty simple you just have to know your stuff see this post: [http://ubuntuforums.org/showthread.php?p=286593#post286593]("http://ubuntuforums.org/showthread.php?p=286593#post286593") (ill get a better list of things to do in 3-4 hrs)[/QUOTE] You mention in that thread to get the latest supplied Ubuntu kernel. Which specific version works for you in AMD64? I used Tamir's 2.6.12-**k8** kernel. Or are you using Ubuntu's 2.6.10-amd64-**k8**? (I have only tried 2.6.10-amd64-**generic** so far... I am planning to roll back to it

[QUOTE=nitinshantharam] I thought CPU scaling WAS working last time i installed ubuntu (Some days ago) - I had the applet up and i was watching it go form 800 - 2000 so i believe thats already working.[/QUOTE] It never complained when I ran "2.6.10-amd64-generic" the CPU Scaling applet just didn't show anything. Perhaps I just need to run the "2.6.10-amd64-k8" (which is specifically for the Turion).

I'll try that tonight and report back.

---

### Post by Cosmic_Crusader on 2005-08-06
I installed the x86 (32 bit) version of Ubuntu 5.04 and not much was different.
 - CPU scaling still did not appear to be working, or at least the panel applet was not showing anything but "-- ?"
 - fglrx still did not work when installing restricted kernel modules
 - Touchpad still does not work without "rmmod psmouse && modprobe psmouse"
 - battery still did not work

I'm going to reinstall 64bit Hoary again and then after updating it, I will install selected packages from the upcoming breezy (mainly the kernel and fglrx).  32bit doesn't appear to have any compelling reason over 64bit.

I'll keep reporting here some notes in case others find it useful or have pointers to help me out.

---

### Post by lakin on 2005-08-12
I have spent the past few days getting Ubuntu working as well as I can with my Ferrari 4005 laptop. 
Here are my notes:

[http://pages.cpsc.ucalgary.ca/~weckerl/ferrari_ubuntu_64.html](http://pages.cpsc.ucalgary.ca/~weckerl/ferrari_ubuntu_64.html)

I would appreciate feedback on this if there are typos or unclear sections.  please continue to use these forums for problems, rather than using my email.

---

