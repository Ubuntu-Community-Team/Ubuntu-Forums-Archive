---
title: "Installation issues"
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by Arif Safwan on 2009-03-22
My dad gave me his old laptop today because he couldn't turn it on any more (not sure if it was a BIOS or a Windows Vista issue). I reformatted the hard drive using Gparted, and then inserted my Ubuntu 8.04 liveCD. When I did, the screen came up with the message

"Error loading operating system_"

What should I do to install Ubuntu on it?

Pre-emptive thanks for your help guys.

AS

---

### Post by tommcd on 2009-03-22
Is the laptop set to boot off the CDROM drive as the 1st boot device? You have to boot from the live CD to run it. The "Error loading operating system" message sounds like you are booting from the now blank hard drive.

---

### Post by Arif Safwan on 2009-03-23
I pressed Esc as I turned it on, and selected CD drive from the menu. 
I also tried going into Setup and changing the boot order. 
Should I have done something else?

---

### Post by tommcd on 2009-03-24
> **Arif Safwan said:**
> I pressed Esc as I turned it on, and selected CD drive from the menu. 
I also tried going into Setup and changing the boot order. 
Should I have done something else?
Did you set your computer's BIOS to boot from the CDROM as *the first boot device*? This is how it should be set.

Also, how did you burn the live CD? You can't just copy the iso file to a CD. You have to burn it as an iso image.  If you are burning the CD from Windows, then try the free programs Iso Recorder or Infra Recorder, and burn the CD at the slowest possible speed. See this:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Then set your computer to boot from the CDROM drive and see if the live CD will boot. When the live CD boots, first choose the option to "check CD for defects"
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck)
If that passes ok then boot up Ubuntu and enjoy!

---

### Post by Arif Safwan on 2009-03-24
Okay, I did another LiveCD for 8.10 using your instructions, and got as far as the LiveCD loading screen. 

Unfortunately, after I select "Install Ubuntu", the screen freezes for about three minutes before coming up with a box titled "I/O error" which reads "Error reading boot CD." and gives the option to Reboot. 
At the top of the screen in green comes the code 8042009F

Unfortunately nothing changes on reboot, and the other options on the menu (including 'check for defects') lead to a simple freeze. High pitched beeps emerge whenever I hit a button during the freeze.

Does anyone know what I should do to fix things? Is it a BIOS problem?

---

### Post by rambocommando on 2009-03-24
Have did you check the MD5 sum on the ISO before you burned it to a CD? You might want to do that if you haven't. Also if you have access to another computer you could try booting it in that computer and doing the 'check cd' option from there.

---

### Post by snowpine on 2009-03-24
"Old laptop" raises a flag. What are the machine's specs, especially ram? 384mb is recommended to install using the Live CD; if you only have 256mb (or less), try the Ubuntu Alternate CD, or a lighter-weight distro (such as Xubuntu).

---

### Post by Arif Safwan on 2009-03-24
I call it old simply because he got a new one on Sunday. It's an HP compaq nx9010. It has a Pentium IV processor, 2.8GHz, and 512RAM.

Going to try the MD5 thing now.

---

### Post by tommcd on 2009-03-24
> **Arif Safwan said:**
> 
Unfortunately nothing changes on reboot, and the other options on the menu (including 'check for defects') lead to a simple freeze. High pitched beeps emerge whenever I hit a button during the freeze.


If you can't even check the CD for defects then either the CD is bad, or the live CD could possibly  have a  problem with your laptop's chipset. You laptop has an ATI chipset according to this:
[http://reviews.cnet.com/laptops/hp-compaq-nx9010-series/4507-3121_7-30474669.html](http://reviews.cnet.com/laptops/hp-compaq-nx9010-series/4507-3121_7-30474669.html)
For the most failsafe install I would get the Ubuntu 8.10 32 bit alternate install CD. Burn the CD with Iso Recorder or Infra Recorder that I linked to in my last post; and burn the disc at the slowest possible speed.  Then check the CD for defects from the main menu when the CD boots up.
The alternate install CD is a text based installer. It will rule out graphics problems with installation. This is not a live CD though. It is just for installing Ubuntu.

---

