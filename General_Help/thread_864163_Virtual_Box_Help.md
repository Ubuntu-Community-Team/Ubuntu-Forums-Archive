---
title: "Virtual Box Help"
date: 2008-07-19
forum: General Help
---

### Post by KingNeil on 2008-07-19
I'm looking to use Virtual Box to run Windows XP, so I can use it for printing basically, and maybe some video editing.

I've installed Virtual Box, I have the WinXP CD, and I've set up the WinXP Virtual Box.

But I can't get it to run. When I run it, I get this error:

[IMG]http://www.upload2world.com/pic93/upload2world_e6aef.png[/IMG]

Can someone help? Surely this must be a simple error right here.

---

### Post by mikewhatever on 2008-07-19
You have to add yourself to vboxusers group either through GUI or using the following commands, where username is your username.
<sudo usermod -a -G vboxusers username>

Here's the link to vbox manual [http://www.virtualbox.org/download/1.6.2/UserManual.pdf](http://www.virtualbox.org/download/1.6.2/UserManual.pdf)

---

### Post by KingNeil on 2008-07-19
I did that and I still get the same error. How do I do it through the GUI?

---

### Post by mikewhatever on 2008-07-19
>   Also note that adding an active user to that group will require that user to log out and back in again. This should be done manually after successful installation of the package.

Have you done that?

---

### Post by KingNeil on 2008-07-19
> **mikewhatever said:**
> Have you done that?

I'm not entirely sure what that meant. Do you mean a log out of ubuntu?

---

### Post by Taxman415a on 2008-07-19
Yes. You need to log out and log back in for your user groups to be re-read and assigned properly.

---

### Post by KingNeil on 2008-07-19
> **Taxman415a said:**
> Yes. You need to log out and log back in for your user groups to be re-read and assigned properly.

OK, excellent. Windows seems to be installing now. I'll post additional messages in this thread if I encounter any installation problems. Thank you for all your help. You have been thanked!

---

### Post by Taxman415a on 2008-07-19
Good to hear. Incidentally, how did you install Virtualbox? The GPL version in the repositories (the one you can install with apt-get, synaptic, etc) doesn't support USB, so if you have a USB printer, you'll need to download SUN's free as in $ but not free as in freedom version that does support USB. Incidentally I still haven't gotten USB working with that version either. I really should try again. The problem is SUN or whoever they bought the code from used an antiquated usb device interface for linux. There are rumors they will GPL the USB part too and that would be really great. Then it could be made much easier to work and updated.

---

### Post by KingNeil on 2008-07-19
Well, I downloaded the deb file from virtualbox.org.

Btw, new question, how do I access the Windows My Documents etc through Ubuntu, cause I might need to occasionally transfer some files? Thanks

[btw amazing how little disk space XP takes up under VirtualBox)

---

### Post by MonctonJohn on 2008-07-19
You can also add the virtualbox repository in the package manager and install the USB capable version that way. There is a guide on the forums somewhere but I don't remember where. I have Kubuntu and I followed the guide and it works perfectly. I used my vm to create a VM that I could install Kubuntu on a USB flash drive.

---

### Post by KingNeil on 2008-07-19
Can anyone help me with sharing my Ubuntu files with Windows?

---

### Post by Oldsoldier2003 on 2008-07-19
> **KingNeil said:**
> Can anyone help me with sharing my Ubuntu files with Windows?

Start Virtualbox, select your Vm and click settings. Then select shared folders from the list on the left. You will be able to add/remove/modify shares.

---

### Post by KingNeil on 2008-07-19
> **Oldsoldier2003 said:**
> Start Virtualbox, select your Vm and click settings. Then select shared folders from the list on the left. You will be able to add/remove/modify shares.

I got that, but I don't know where to find the folder in Windows.

---

### Post by gunthr on 2008-07-19
You have to map the drive using *net use.*

---

### Post by KingNeil on 2008-07-19
> **gunthr said:**
> You have to map the drive using *net use.*

Can you elaborate on that?

And btw, just one more error. Windows has no access to my USB ports, which can be seen when I click Settings on my WinXP installation in Virtual Box, and get the following error:

[img]http://www.upload2world.com/pic93/upload2world_955fc.png[/img]

---

### Post by fiddledd on 2008-07-19
The command is "net use x: \\vboxsvr\sharename" where "x" is the drive letter you want to use and "sharename" is the name you used when you set up the shared folder in VirtualBox. You run the command in the Guest btw.

---

### Post by KingNeil on 2008-07-19
> **fiddledd said:**
> The command is "net use x: \\vboxsvr\sharename" where "x" is the drive letter you want to use and "sharename" is the name you used when you set up the shared folder in VirtualBox. You run the command in the Guest btw.

OK, I know I'm absolutely sounding like a n00b now, but it can't find that location (I've replaced sharename). Any way to know where to find the directory?

---

### Post by gunthr on 2008-07-19
Maybe this will help with your USB issue. The first section refers to that error.


[http://paulsiu.wordpress.com/2007/11/20/tips-on-running-innotek-virtualbox/](http://paulsiu.wordpress.com/2007/11/20/tips-on-running-innotek-virtualbox/)

---

### Post by gunthr on 2008-07-19
You would have to create that directory as well as point to it in the guest shared folder settings. I created a folder in my home directory called vbox_share and then pointed to it in the shared folders config for the guest.

---

### Post by KingNeil on 2008-07-19
> **gunthr said:**
> Maybe this will help with your USB issue. The first section refers to that error.


[http://paulsiu.wordpress.com/2007/11/20/tips-on-running-innotek-virtualbox/](http://paulsiu.wordpress.com/2007/11/20/tips-on-running-innotek-virtualbox/)

When I open that file and edit as the guide says, it says I don't have the permissions to save as.

How would I go about opening this in the terminal?

---

### Post by gunthr on 2008-07-19
```
sudo vim filename
```

or 

```
sudo gedit filename
``` for a gui based editor.

---

### Post by KingNeil on 2008-07-19
> **gunthr said:**
> ```
sudo vim filename
```

or 

```
sudo gedit filename
``` for a gui based editor.

I edited the first file, uncommenting the code. But then with the second file, the section described does not exist:

> 
Even though you enabled usbfs, the user do not have permission to use USB. You can set up a rule to give each user access. Because everyone who use Virtualbox has to be in the group vboxusers. The easiest way to give every Virtualbox user access would be to give vboxusers access. Sudo edit the file /etc/udev/rules.d/40-permissions.rules, locate the following line:

# USB devices (usbfs replacement)
SUBSYSTEM==”usb_device”, MODE=”0664&#8243;
Change the line to:

# USB devices (usbfs replacement)
SUBSYSTEM==”usb_device”, GROUP=”vboxusers”, MODE=”0664&#8243;


None of that exists within the 40-permissions.rules file

---

### Post by gunthr on 2008-07-19
It's in:

/etc/udev/rules.d/40-basic-permissions.rules

---

### Post by mikewhatever on 2008-07-19
> **KingNeil said:**
> Can you elaborate on that?

And btw, just one more error. Windows has no access to my USB ports, which can be seen when I click Settings on my WinXP installation in Virtual Box, and get the following error:

It looks like my suggestion to read vbox manual had gone unnoticed. Everything you want is there in plain English.

> 2.3.3 USB and advanced networking support
In order to use VirtualBox&#8217;s USB support, the user account under which you intend torun VirtualBox must have read and write access to the USB filesystem (usbfs).
  In addition, access to /dev/net/tun will be required if you want to use Host Interface Networking, which is described in detail in chapter 6.5, Introduction to Host Interface Networking (HIF), page 73.

---

### Post by KingNeil on 2008-07-19
> **gunthr said:**
> It's in:

/etc/udev/rules.d/40-basic-permissions.rules

The correct line still doesn't exist. A line very similar existed. Anyway, I tried replacing it and still the USB seems to fail.

I'm considering a full-blown switch back to Windows, because I REALLY need a way to print and properly edit video.

---

### Post by KingNeil on 2008-07-19
> **mikewhatever said:**
> It looks like my suggestion to read vbox manual had gone unnoticed. Everything you want is there in plain English.

> 
2.3.3 USB and advanced networking support
In order to use VirtualBox’s USB support, the user account under which you intend torun VirtualBox must have read and write access to the USB filesystem (usbfs).
In addition, access to /dev/net/tun will be required if you want to use Host Interface Networking, which is described in detail in chapter 6.5, Introduction to Host Interface Networking (HIF), page 73. 




I still can't figure out how to do any of that stuff.

---

### Post by mikewhatever on 2008-07-19
> **KingNeil said:**
> I still can't figure out how to do any of that stuff.

That's because you need to download the pdf file and read it.):P

---

### Post by KingNeil on 2008-07-19
Screw it. I'm going back to Windows. Ubuntu takes longer to boot anyway.

---

### Post by gunthr on 2008-07-19
Here's another link that has a few more steps. I don't have time to look into the manual, but maybe it details what you need to do. I'll be setting up 1.6.2 this afternoon on Hardy and will probably run into the same issues. If I do and get it working, I'll post it here. Good luck.

[http://linuxchronicles.wordpress.com/2008/05/28/ubuntu-got-usb-in-virtualbox-160/](http://linuxchronicles.wordpress.com/2008/05/28/ubuntu-got-usb-in-virtualbox-160/)

---

### Post by gunthr on 2008-07-19
> **KingNeil said:**
> Screw it. I'm going back to Windows. Ubuntu takes longer to boot anyway.

Seems to me, your going about fixing this the right way by asking questions when you don't understand something. It's just a shame that not everyone is willing to help without the snide remarks.

---

### Post by KingNeil on 2008-07-19
Once Ubuntu gets its printer drivers and video editing sorted out, I'll be back here quicker than you can say "Linus Torvalds".

But for now, I won't go back quite as horrific as Windows Vista, but stick with the not-quite-so-bad XP. Thanks anyway.

---

