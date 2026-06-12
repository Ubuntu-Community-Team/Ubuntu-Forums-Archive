---
title: "grub error"
date: 2009-01-29
forum: Installation &amp; Upgrades
---

### Post by dconnors on 2009-01-29
hi.. i have an infamous  hp dv6000 lappie..  and 
had a previous install of ubuntu 64 , dual boot with windows vista, installed on one partitioned hard drive where
c: is the standard windows drive.. 

until doing a complete update to ubuntu  8.04 lts, 
the 'puter booted up fine into grub and I could choose 
which os to run. 

I did all the updates to my installed linux install 
and got the message  an update is available to 8.04 lts. 

it completed and powered down.. now I'm getting a grub 
error message  

error: 17 and it freezes there.  
I can't even boot into windows.  I managed to use a live cd 
of 8.1 to get the lappie running.. booting from the cd only, and I copied all my files onto a usb stick..  so the drive and all the windows files are still there..  I'm an idiot when it comes to linux directorys  so i can't tell if the linux directorys I'm looking at are from the live cd  or the hard drive(sorry)
 I even tried installing 8.1 from the live cd.. but it hacks up a hair ball when it comes to partitioning. and won't proceed. 


so in a nutshell  I'm looking for a work around to deal with the machine hanging  at grub  error 17. 

thanks

dc

---

### Post by zxscooby on 2009-01-29
Try using the information found here.

[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by caljohnsmith on 2009-01-29
[QUOTE=dconnors]but it hacks up a hair ball when it comes to partitioning. and won't proceed.[/QUOTE]
That's not a good sign, what exactly do you mean "hacks up a hair ball"? When you get to the partitioning stage of the installer, does it simply not show your existing partitions? I think it would help greatly if we could get a better picture of your setup related to booting, so how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by dconnors on 2009-01-30
ok.. I'll work on that, sorry  it basically  stops and tells me that the partition i've chosen doesn't have enough room and to resize to a size in kbytes  that seems bigger than my hard drive.. will be working on clarifying.. thanks

cheers

dale c.

---

