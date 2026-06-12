---
title: "blank screen when booting and problem with OpenOffice"
date: 2008-02-19
forum: Hardware &amp; Laptops
---

### Post by kavoura on 2008-02-19
I recently convinced a friend to install Ubuntu on her HP laptop (Omnibook xe4500) and we went ahead and did that. However, when the laptop boots up, the normal splash screen with the Ubuntu logo and the orange progress bar do not appear, instead the screen is just blank.

Model: HP Ominbook xe4500
Processor: Pentium 1.7 GHz
Wireless Card: none
Graphics Card: built in ATI
Gutsy Tribe (Version): 7.10, installed from a DVD-ROM that came with a magazine called Linux Format

I installed the same version of Ubuntu on my PC at home and have had no problems like this with it. I also did a second installation on another PC, which is also okay, but as the DVD-ROM comes with KDE files as well as Gnome, I set it up on the second PC as KDE and it loads up with the Kubuntu logo splash screen.

Anyway, on my friend's PC, being new to Linux, she chose to use KDE, as it is more like Windows than Gnome is.

But whether logging in using Gnome or KDE, the boot up sequence just gives a blank screen.

Sequence:
Turn on laptop, normal text appears and HP logo. 
Grub boot menu appears with Ubuntu and Windows XP listed.
Select Ubuntu or just wait to boot by default into Ubuntu.
Screen goes blank, but hard disk light is flashing.
After a while, the Ubuntu login screen appears, enter username and password and log in (no more problems with the screen), until logging out and shutting down, then screen goes blank again instead of seeing Ubuntu logo.

There is also another problem in OpenOffice. When running OpenOffice (in KDE), the icons on the toolbars are replaced with text. 

So, what can be done to fix these problems? I assume that there is a simple change to the Grub options in menu.lst that would fix the boot up screen?
But what about the OpenOffice problem? Is that caused by using KDE instead of Gnome? Is there an update or piece of software that needs to be installed to make OpenOffice work properly with Ubuntu running KDE?

On the plus side, when she boots into Windows XP the sound is awful and sounds very broken. I did think that maybe it was faulty hardware, but when booting into Ubuntu the sound is crystal clear and without any problems. Ubuntu is definitely better than Windows.

---

### Post by Existentialist on 2008-02-19
Try changing the resolution of the splash screen to whatever you display is set at.This example would be for a 1024x768 screen resolution. Edit:
/etc/usplash.conf

and add:

xres=1024   (or whatever yours is)
yres=768     (again match your settings)

then run:

sudo update-usplash-theme usplash-theme-ubuntu

If this doesn't work, try it at 1024x768, as that should.  If this doesn't work, make sure to check the menu.lst at:

/boot/grub/menu.lst

to make sure that your option for Ubuntu has the parts in bold below:

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=d1f8e8ae-d388-41d8-bdfb-3119113b0f96 ro quiet **splash**
initrd /boot/initrd.img-2.6.22-14-generic
quiet

---

### Post by kavoura on 2008-02-24
Today I got the chance to look at my friend's laptop again. I checked the usplash.conf file, and the settings were incorrect, they were set to 1280 and 1024, so I changed them to 1024 and 768 and ran the command 

sudo update-usplash-theme usplash-theme-ubuntu

Then when shutting down the laptop the Ubuntu splash screen appeared, and it was there again as it should be when booting up.

Thanks for your help.


Now, as for OpenOffice, there is still a problem, but only when using KDE, it is okay when using Gnome, so I guess there is a problem there with KDE. Also, it now has problems with Firefox. There is a list of Add-ons installed, but none of them are active, they cannot be updated nor uninstalled.

The laptop itself started off running Windows XP Pro. I repartitioned and installed Ubuntu, and then copied the bookmarks from the Windows installation of Firefox to the Ubuntu installation. I am wondering if perhaps the add-ons listed in Firefox in Ubuntu are actually those installed in Windows and somehow it is picking those up. I tried uninstalling and reinstalling Firefox (and deleting all settings in the user's home account in Ubuntu for Firefox) but it made no difference.

---

### Post by Existentialist on 2008-02-24
Whenever I have done a reinstall I have just copied over the whole profile for firefox.  That way all of the bookmarks, preferences, and add-ons are transfered also.  This has worked going from xp to ubuntu and vice-versa.  It seems like you may have gotten part of the profile transfered which has what add-ons are installed, but not the actual add-ons.  If you haven't gotten rid of thew windows partition already, take the whole contents of the firefox profile you want to use, and copy the contents over the files in the profile being used by firefox in your ubuntu installation (back it up first, just in case).

---

### Post by Hagar Delest on 2008-02-26
For OpenOffice.org, make sure that all the icons themes are installed in Synaptic : openoffice.org2-style-... packages.

---

### Post by kavoura on 2008-03-09
Thanks, Hagar de l'Est, your suggestion worked. When I visited my friend, I looked in synaptic for icons for KDE and OpenOffice, installed those and now OpenOffice looks great.
I also installed MS Office 2000 via CrossOver, as she had MS Office 2000 in Windows XP, and needs to use it for work (she teaches in a college where they use MS Office, although a later version). That works well too, but when she opened a Powerpoint file in MS Office, being used to using Office 2003, the layout of the screen was different, but when using OpenOffice it looked much more like the MS Office 2003 she was used to, so she used that instead!

---

