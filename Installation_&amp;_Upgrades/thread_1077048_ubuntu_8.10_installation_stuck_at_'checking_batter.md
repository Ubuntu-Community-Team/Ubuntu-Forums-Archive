---
title: "ubuntu 8.10 installation stuck at 'checking battery state'"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by bilmas on 2009-02-22
initially i tried to install ubuntu alongside windows on a separate partition but i was not getting the option to shrink the partition to make way for a new one beyond 8 mb so after a couple of days of thinking it over i decided that there is nothing that i absolutely need windows for.  my desktop is only used for internet and music both of which are obviously possible on ubuntu

so i went to install ubuntu as my only operating system.  the installation starts to go through the motions.  at one point in the installation a black screen comes up saying it is testing certain things and then the progress bar reappears.  when it gets to about 59%, though, i get a black screen that says '* Cecking battery state... [OK]' and it does not allow me to pass this.  sporadically a blue screen will appear saying that the display has been reset six times in under two minutes etc

i am trying to install ubuntu 8.10.  i am currently downloading ubuntu 8.04 to burn to a disc on my mac to try that out but does anybody have any suggestions should this happen again?

---

### Post by tommcd on 2009-02-22
Some troubleshooting first.
Boot up the Ubuntu CD and choose the option "check CD for errors". Does the CD pass the test?
How did you burn the CD? You may want to burn the CD with Iso Recorder or Infra Recorder:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Be sure to burn at the slowest possible speed. Then boot up the newly burned CD and check it for defects.

What are the specs of your computer?

---

### Post by bilmas on 2009-02-22
my computer?  old.  6 years old.  but more seriously: pentium 4 1.2 ghz, 512 mb ram and windows xp.

my only option now is to burn the disc on my mac.  will that work on the pc still?

edit: i just did a disk check and the disk was found to be error free

also i have been burning this to a dvd+rw since i only have blank dvd discs.  would this make a different?

---

### Post by bilmas on 2009-02-22
other threads on similar topics suggested that the nvidea driver be installed.  i have an ati-radeon i believe but could something similar help?

---

### Post by tommcd on 2009-02-22
Since it fails on "checking battery state" I assume this is a laptop. Is that correct? What is the specific brand and model number of your computer?

This *may* be an acpi problem. When you boot the Ubuntu CD, hit F6 to load other boot options. At the end of the boot line that appears, type "acpi=force pci=noacpi" (include the quotes) and hit enter to see if you can now install. If this does not work, boot the CD again, hit F6, and enter "acpi=off".
I don't think burning the CD on the Mac will help. If you want to burn the CD again try Iso Recorder or Infra Recorder, and burn at the slowest possible speed.

As far as using dvd+rw discs is concerned, I have noticed that when burning linux iso discs with cd-rw discs that after the disc has been written and rewritten to a lot of times that the md5sum check will fail (md5sum check is what the "check CD for defects" option does). You might try burning with a cd-r or dvd-r and not a -rw disc. But if the disc passed with no errors this may not help.
The only other option I can think of (to rule out a graphics problem) would be to try installing from the Ubuntu alternate install CD. This is text based installer, but it is fairly easy to follow and will give you the same Ubuntu when finished.

---

### Post by bilmas on 2009-02-22
> **tommcd said:**
> Since it fails on "checking battery state" I assume this is a laptop. Is that correct? What is the specific brand and model number of your computer?

This *may* be an acpi problem. When you boot the Ubuntu CD, hit F6 to load other boot options. At the end of the boot line that appears, type "acpi=force pci=noacpi" (include the quotes) and hit enter to see if you can now install. If this does not work, boot the CD again, hit F6, and enter "acpi=off".
I don't think burning the CD on the Mac will help. If you want to burn the CD again try Iso Recorder or Infra Recorder, and burn at the slowest possible speed.

As far as using dvd+rw discs is concerned, I have noticed that when burning linux iso discs with cd-rw discs that after the disc has been written and rewritten to a lot of times that the md5sum check will fail (md5sum check is what the "check CD for defects" option does). You might try burning with a cd-r or dvd-r and not a -rw disc. But if the disc passed with no errors this may not help.
The only other option I can think of (to rule out a graphics problem) would be to try installing from the Ubuntu alternate install CD. This is text based installer, but it is fairly easy to follow and will give you the same Ubuntu when finished.

it is a desktop, not a laptop.  i am trying an install of 8.04 as we speak.  thanks for the tips.  i will let you know what happens.

---

### Post by tommcd on 2009-02-22
> **bilmas said:**
> it is a desktop, not a laptop.  i am trying an install of 8.04 as we speak.  thanks for the tips.  i will let you know what happens.
The reason I asked about the specs of your computer is that it may be helpful to know the motherboard chipset of your computer. When you boot the Ubuntu live CD open a terminal (applications > accessories > terminal) and run:
```
sudo lspci -v
```
and post the output here.
Or if you know the motherboard chipset please post it. Since you have an Intel CPU I would assume it is an Intel chipset; but it could be Via or Sys or something else given the age of your computer. A 6 yr old Pentium PC with 512 mb ram should not be a problem for running Ubuntu though.

Also try the acpi boot options I gave in my last post.

---

### Post by Guus1982 on 2009-02-22
May i join in on this topic? 

Ive downloaded the live cd file and installed it on my laptop as in dual boot (toshiba satelite 100/a). So far so good. After that i wanted to instal it on my laptop HP nc4400 and there it went bad. I was also trying to create a dual boot but when ubuntu tried to create a partrition the setup crased and on rebooting i recieved the information that my partition was damaged. After restoring the harddrive which was erased completely i tried to install ubuntu again. 

For the record this laptop does not have an cd drive, so i created an bootable usb stick with the ubuntu install on the other laptop.

But now im stuck: every time i boot from the usb stick it shows the progression bar and then gives me this message:

"setupcon: None of /etc/default/console-setup nor /.console-setup exists
Checking Battery State OK"

and then nothing happens...

What to do from here?

---

### Post by tommcd on 2009-02-22
> **Guus1982 said:**
> 
For the record this laptop does not have an cd drive, so i created an bootable usb stick with the ubuntu install on the other laptop.


I have never installed Ubuntu from a usb drive. Here is the official documentation on installing Ubuntu from a usb drive. You may also try the UNetbootin method described there:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Guus1982 on 2009-02-23
i figured out what the problem was for me:
[http://ubuntuforums.org/showthread.php?p=6784153#post6784153](http://ubuntuforums.org/showthread.php?p=6784153#post6784153)

---

