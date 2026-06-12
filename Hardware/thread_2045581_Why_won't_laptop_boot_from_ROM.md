---
title: "Why won't laptop boot from ROM?"
date: 2012-08-21
forum: Hardware
---

### Post by PromoTheRobot on 2012-08-21
I have an Acer Aspire laptop with Windows Vista.  I burned a disc with UBUNTU 12-04 and placed it in the DVD-ROM drive.  I went to my BIOS settings and made the DVD-ROm #1 in boot order.  But no matter if a restart or start from completely off, the laptop keeps starting Vista.  The DVD-ROM spin during boot up but no UBUNTU.  Any ideas what is going wrong here?

---

### Post by OM55 on 2012-08-21
Hello PromoTheRobot,

That usually means that the CD you burnt may not be bootable. When you burn it there should be a separate option to 'make it bootable' which must be checked.
Did you just copy the Ubuntu 12.04 ISO to the CD or specifically made it bootable?

If you use a Window CD burner, you should have an option to "Make CD bootable", remember to check this option..

If you use Ubuntu itself to create the Ubuntu Live CD (although i assume you didn't, here is the info anyway...), you can use Startup Disk Creator (in gnome-session-fallback it will be under: Applications -> System Tools -> Administration -> Startup Disk Creator. Alternatively, in terminal type: usb-creator-gtk) 

Another option would be to install UNetbootin which will do the job as well:
```
sudo apt-get install unetbootin
```

---

### Post by PromoTheRobot on 2012-08-21
Thanks for the info, but I'm having a bit of trouble with this.  The CD burning application built into Windows 7 (my desktop) does not give me an option to make the disc bootable.  Another program, CyberLink Power2Go, does give me that option but requires a "boot image" img file.  I have no idea what that is or where to find it, and the program will not proceed without it.

---

### Post by OM55 on 2012-08-21
I am not familiar with CyverLink Power2Go but according to the feature description of CyberLink Power2Go, is does support ISO ([http://www.cyberlink.com/products/power2go/burning_en_CA.html](http://www.cyberlink.com/products/power2go/burning_en_CA.html)), so could be that you just need to change a selection somewhere from IMG to ISO. But could also be that the version you have is older or limited and does not have that option.

Here are a few links that would help you get it burnt as a bootable CD, within Windows (I haven't used Windows for quite a while, so am not familiar with any of the programs here, but found reviews claiming they are fine):

ImgBurn - Freeware. Install and burn the ISO as a bootable CD.
[http://www.imgburn.com/](http://www.imgburn.com/)

UltraISO - Very cheap ($25) and has a free evaluation option, so could be that during evaluation it will allow you to burn a complete bootable CD
[http://www.ezbsystems.com/ultraiso/](http://www.ezbsystems.com/ultraiso/)

UltraISO - Explanation on how to use it
[http://www.youtube.com/watch?v=z7rRsQGew28](http://www.youtube.com/watch?v=z7rRsQGew28)

Using only Windows free additional software:
[http://techtips.salon.com/burn-boot-cd-windows-13210.html](http://techtips.salon.com/burn-boot-cd-windows-13210.html)

---

### Post by PromoTheRobot on 2012-08-21
Okay. I figured out what I was doing wrong with Power2Go.  So I now have a boot disc of Ubuntu 12.04.  So I load it and I get a message that says "Operating System load error" for about a second before it continues on to Vista.  

Maybe this old laptop doesn't like 12.04?  So I burn a boot disc with Ubunta 11.04 beta.  This time I get an endless blinking cursor.  In fact I waited 20 minutes and all it did was blink the cursor all that time.

This Acer laptop is determined to foil me at every turn.  Any more suggestions before I give up?

---

### Post by OM55 on 2012-08-21
Unless your laptop is over 10 years old (and maybe even then) it should be able to load and run Ubuntu 12.04 Live CD... In fact I use ONLY Acer laptops and have currently about 15-20 installations of them, new and old (10 years) doing different functions - all working just fine.
so I suspect it is more likely the burning procedure and CDs.

I would suggest to try again and use ImageBrn ([http://www.imgburn.com/](http://www.imgburn.com/)) or UltraISO ([http://www.ezbsystems.com/ultraiso/](http://www.ezbsystems.com/ultraiso/)) to burn your CD. Remember to use a NEW cd and select ***"close the session"*** option if available. "Open session" refer to leaving the rewritable CD open for further re-writes. But some old CD drives do not know how to read rewritable CDs with open sessions.

If that still doesn't work, have you considered creating a bootable USB (not a CD)?

I attached to this message a small Windows utility called '**MakeDisk**' (in a zip file) that will create a bootable USB media from an ISO file. The instructions are included.

If you are given the option to select between HDD USB or USB KEY - select HDD USB (which is more likely to be recognized by all computers, old and new).

Remember that you will also need to change the BIOS settings again so the USB HDD is first to boot from. BUT you can do that only when the USB media is inserted into the USB slot or otherwise it will not show up on the list of bootable devices.

Hope this will help!

---

