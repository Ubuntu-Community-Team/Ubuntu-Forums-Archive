---
title: "install minimal w/o internet"
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by scales on 2009-06-19
Hi all, i would like to install the cli version of ubuntu without having to download all the install packages etc from online because my internet is pretty slow.  i cannot seem to find a way to do this, any advice? The "cli" install from the alternate disc wants to get all the files from the web...WHY!?

---

### Post by boof1988 on 2009-06-19
> **scales said:**
> Hi all, i would like to install the cli version of ubuntu without having to download all the install packages etc from online because my internet is pretty slow.  i cannot seem to find a way to do this, any advice? The "cli" install from the alternate disc wants to get all the files from the web...WHY!?

If you (or have you already tried?) unplug the ethernet cable the installation may not try to download packages.  And then you can get all the appropriate updates later if you want them.

I think the reason the installer tries to install some packages from the mirror is so you have all of the updated packages.  There will be some packages that have updates even though you are only installing a CLI system.

Also... You can install packages from the Alternate Installation CD by adding to your sources (though the packages may not be the most current since you are using the packages on the CD and not downloading the packages from a mirror).  To add the CD as a source (you will then need to have the disk in the drive whenever you want to add packages unless you remove it from the sources list)...

```
sudo apt-cdrom add
```

References:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[https://help.ubuntu.com/community/Installation/LowMemorySystems#Install an Ubuntu command-line system](https://help.ubuntu.com/community/Installation/LowMemorySystems#Install an Ubuntu command-line system)
[https://help.ubuntu.com/community/Installation#Installation using the Alternate CD](https://help.ubuntu.com/community/Installation#Installation using the Alternate CD)
[https://help.ubuntu.com/community/AptCdrom](https://help.ubuntu.com/community/AptCdrom)

---

### Post by scales on 2009-06-19
well the CLI install wants to configure my network so it can download packages, it is set in the procedure.  i can open another shell in another session and peek around but there is no /etc/apt/ dir and therefore no sources.lst to change.  i just want to install a minimal ubuntu quickly since the install from network took ages to finish.  once ubuntu is installed then i can worry about upgrading etc.   any way to get around the install trying to download packages?

---

### Post by boof1988 on 2009-06-19
> **scales said:**
> well the CLI install wants to configure my network so it can download packages, it is set in the procedure.  i can open another shell in another session and peek around but there is no /etc/apt/ dir and therefore no sources.lst to change.  i just want to install a minimal ubuntu quickly since the install from network took ages to finish.  once ubuntu is installed then i can worry about upgrading etc.   any way to get around the install trying to download packages?

[LIST]
[*]Is your ultimate installation goal to (only) have a CLI installation on the machine?
[*]Or do you want to have the full Ubuntu Desktop/GUI etc?
[*]What (Ubuntu) installation media do you currently have?
[/LIST]

> **scales said:**
> ...i just want to install a minimal ubuntu quickly...

When you say "minimal ubuntu", do you mean that you want to install the CLI and then add your preferred desktop/window-manager?  If that is the case then I can try to walk you through (step-by-step as best I can) the installation of the CLI system and then other packages you want.  And this can be done from the ubuntu-<version>-alternate-<architecture>.iso (your alternate install CD) if you have one.

Let me know...

---

### Post by scales on 2009-06-19
ok here are the specifics.  I recently tried archlinux and while it was good to learn a few things, it was a bit of a pain to setup.  my ideal setup would be ubuntu with say slim as a login manager, then to have compiz and lxpanel.  i did this in arch but for some reason my audio did work and then stopped cooperating.  i have used ubuntu-desktop for a while now and my sound never failed me there so i wanted to go back to it but miss the slim and sleek setup.  i have an eeepc1000he and use a bootable usb to get ubuntu cli up and running but for whatever reason it always insists on connecting to the web first to download stuff and it takes forever to finish.  i would also like to have openbox installed just incase compiz decides to be goofy or whatever.

any thoughts?

---

### Post by boof1988 on 2009-06-20
> **scales said:**
> ok here are the specifics.  I recently tried archlinux and while it was good to learn a few things, it was a bit of a pain to setup.  my ideal setup would be ubuntu with say slim as a login manager, then to have compiz and lxpanel.

Once I have the CLI installation completed, I usually install [LXDE (in Jaunty repos)](http://packages.ubuntu.com/jaunty/lxde) by using the following...

```

sudo apt-get update
sudo apt-get install lxde xinit

```

This gives an installation with basic file management and notepad.

Then you can add anything you want.

> **scales said:**
>   i have used ubuntu-desktop for a while now and my sound never failed me there so i wanted to go back to it but miss the slim and sleek setup.

I like to use the Ubuntu CLI install as well.

> **scales said:**
>   i have an eeepc1000he and use a bootable usb to get ubuntu cli up and running but for whatever reason it always insists on connecting to the web first to download stuff and it takes forever to finish.

When installing from the Alternate Installation, it will usually take longer than while using the Desktop Installer (IIRC).

But if you unplug your network cable or (if it's available) flip the switch to turn off the wireless network, the Ubuntu installation will just continue without configuring network settings (in my experience).

Once this is done you can update at anytime.  By letting it download the updates whenever you want or by using [APTOnCD](http://packages.ubuntu.com/jaunty/aptoncd) (from the same Ubuntu version but on another installation) to supply the updates/packages.

> **scales said:**
>   i would also like to have openbox installed just incase compiz decides to be goofy or whatever.

I don't have any experience with [openbox](http://packages.ubuntu.com/jaunty/openbox) (since I use LXDE as indicated above).  You can use any one you want.  I don't know if [compiz](http://packages.ubuntu.com/jaunty/compiz) is installed with lxde-core or not.

---

### Post by scales on 2009-06-20
Excellent! i will try it out tonight.  Also i have decided that i dont need compiz, it is a little laggy anyway not quite as functional as i would like.  LXDE is a great choice, i prefer it actually so that is perfect.  I will be sure to report on my experience later.  Thanks!

---

### Post by boof1988 on 2009-06-20
> **scales said:**
> Excellent! i will try it out tonight.  Also i have decided that i dont need compiz, it is a little laggy anyway not quite as functional as i would like.  LXDE is a great choice, i prefer it actually so that is perfect.  I will be sure to report on my experience later.  Thanks!

Keep us posted on how it goes.

If you (or anyone) is interested in the [LXDE Live Desktop](http://lxde.org/download) you (they) can try it out.  I have downloaded it and tried it but I still prefer Ubuntu due to my familiarity with it.

---

### Post by scales on 2009-06-21
> **boof1988 said:**
> But if you unplug your network cable or (if it's available) flip the switch to turn off the wireless network, the Ubuntu installation will just continue without configuring network settings (in my experience).

I am afraid that the CLI version of ubuntu from the "alternate install disc" requires an internet connection.  Whats more is that it has to be wired since there are no wifi drivers loaded during the install. bummer.

---

### Post by boof1988 on 2009-06-21
> **scales said:**
> I am afraid that the CLI version of ubuntu from the "alternate install disc" requires an internet connection.

I just installed a CLI system using the *ubuntu-9.04-alternate-i386.iso* (burnt to CD) and during the DHCP setup phase I had to choose something like "Do not configure the network now" or "Configure the network connection later".  These options were shown after I chose the "Continue" option after the installer informed me that the DHCP network could not be configured (because the network cable was unplugged.

Did you see an option for "Continue" and then (after the installer figured out that the network can't be configured automatically) another option something like "Configure the network connection later"?

I will try (if I have time and the ability) to install VirtualBox and then install the CLI system that way so I can post a screen-shot of the appropriate screens to let you know what I am talking about.

> **scales said:**
> Whats more is that it has to be wired since there are no wifi drivers loaded during the install. bummer.

Hopefully we can get your system installed without the network connected.  Though I don't know how difficult it is to set up the network after the system is installed.  *dunno*  Guess I'll find out if I'm able to use VirtualBox to do this learning experiment.

---

### Post by boof1988 on 2009-06-21
> **scales said:**
> I am afraid that the CLI version of ubuntu from the "alternate install disc" requires an internet connection.  Whats more is that it has to be wired since there are no wifi drivers loaded during the install. bummer.

After installation of [VirtualBox](http://www.virtualbox.org/wiki/Linux_Downloads) (to test the installation and allow easy screenshots) the following is provided.

The VirtualBox version is...

```
virtualbox-2.2_2.2.4-47978_Ubuntu_jaunty_i386.deb
```

The Ubuntu installation version used is...

```
ubuntu-9.04-alternate-i386.iso
```

[LIST=1]
[*]Ensured network interface is disabled (disabled in virtualbox)
[*]Booted *ubuntu-9.04-alternate-i386.iso* in VirtualBox and chose language
(SEE: InstallUbuntu.png)
[*]Pressed <F4> to bring up installation modes
[*]Selected "Install a command-line system"
(SEE: ChooseCLIInstallation.png)
[*]Pressed <Enter> to close the menu
(SEE: InstallUbuntu.png)
[*]Select "Install Ubuntu" then pressed <Enter> to start installation
[*]Went through a few unrelated screens
[*]"Network autoconfiguration failed" screen displayed
(SEE: NetworkAutoconfigurationFailed.png)
[*]Selected "Continue" and pressed <Enter>
[*]Chose the "Do not configure..." (bottom) option and pressed <Enter>
(SEE: DoNotConfigurNetworkAtThisTime.png)
[*]Hostname request window is displayed
(SEE: EnterHostName.png)
[*]Proceeded with installation as usual
[/LIST]

Hope this helps a little with the details of the process.  If your screens do not show the same options, then I'm not sure how to do the installation.  If you can give more information on what options are displayed during your installation, I may be able to help more. even if the options are not the same as those for my installation.

EDIT:
To set up the network after the installation (using Ubuntu Community Documentation [Network Configuration Page](https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html)) the following was performed...

[LIST=1]
[*]Ensured the network interface is enabled in VirtualBox
[*]Opened the following file for editing
```
sudo nano /etc/network/interfaces
```
[*]Added the following lines to the file /etc/network/interfaces
```
auto eth0
iface eth0 inet dhcp

```
[*]Rebooted the system so that the system would configure the network
[*]Ran the following to ensure the network is configured and the system can download updates/packages
```
sudo apt-get update
```
[/LIST]

---

### Post by scales on 2009-06-21
well i certainly appreciate the effort and help you have been so far boof1998, i did try those same steps. I chose to proceed without the network configured too.  after that i am able to input my host name, but then it asks for a mirror and i select ubuntu.us.blahblah.  it fails when connecting the repo, for obvious reasons, but i am unable to get past that.  if you feel like checkin it out that would be fine and we could doublecheck to make sure i have the right disk.  thanks again :)

---

### Post by boof1988 on 2009-06-21
> **scales said:**
> well i certainly appreciate the effort and help you have been so far boof1998, i did try those same steps. I chose to proceed without the network configured too.  after that i am able to input my host name, but then it asks for a mirror and i select ubuntu.us.blahblah.  it fails when connecting the repo, for obvious reasons, but i am unable to get past that.  if you feel like checkin it out that would be fine and we could doublecheck to make sure i have the right disk.  thanks again :)

Which one of the following (if any) disks are you using to install?

[LIST=1]
[*]The *mini.iso* from the link at Ubuntu Community [MinimalCD Page](https://help.ubuntu.com/community/Installation/MinimalCD) or maybe directly from the mirror (IIRC this installation disk is a network install disk and so it needs a network to complete the installation).
-or-
[*]The *ubuntu-9.04-alternate-i386.iso* from any of the assorted mirrors.  This disk does not need network connection to finish the installation.
[/LIST]

I will try installing Ubuntu in VirtualBox with the *mini.iso* and see if the results are similar to your's.

If you are using the *mini.iso* (which is not the same as *ubuntu-9.04-alternate-i386.iso*, that could be the reason you are needing the network connection to finish the installation.

---

### Post by boof1988 on 2009-06-21
Here are the results for the installation (using the mini.iso).

[LIST=1]
[*]The NoNetworkInterfacesDetected.png screen is displayed
[*]I chose "Continue" and pressed <Enter> and then input a hostname and pressed <Enter> again.
[*]Then I chose a country
(SEE: ChooseAMirrorOfTheUbuntuArchive.png)
[*]Then ChooseAMirrorOfTheUbuntuArchive01.png screen is displayed.
[*]Then I chose the only mirror available.
(SEE: ChooseAMirrorOfTheUbuntuArchive02.png)
[*]Then (since there is no network yet) I chose "Continue" and pressed <Enter>.
(SEE: ChooseAMirrorOfTheUbuntuArchive02.png)
[*]Then ChooseAMirrorOfTheUbuntuArchive03.png screen is displayed
[*]Then the installer takes me back to ChooseAMirrorOfTheUbuntuArchive.png.
[/LIST]

So it seems that the network needs to be available to use the *mini.iso* for installation (maybe this is the CD you have been using?) but the network is not needed when using the *ubuntu-9.04-alternate-i386.iso* to install (maybe this is the one you need to use?).

---

### Post by boof1988 on 2009-06-21
Sorry to post again but each post is limited to 5 attachments.

I have attached the screenshots for the startup screen of the *mini.iso* (network installer) and the *ubuntu-9.04-alternate-i386.iso* (alternative installer) for you to compare to the images you see when you try to install.

---

### Post by scales on 2009-06-21
ok well.  i definately am using the alternate disc, but i am booting off my usb.  i downloaded the jaunty-alternate.iso, and used unetbootin to get it onto my usb drive.  i definately am not able to install from offline though...wonder why...

---

### Post by boof1988 on 2009-06-22
> **scales said:**
> ok well.  i definately am using the alternate disc, but i am booting off my usb.  i downloaded the jaunty-alternate.iso, and used unetbootin to get it onto my usb drive.  i definately am not able to install from offline though...wonder why...

This is confusing to me...  I'll try to install unetbootin, put the *ubuntu-9.04-alternate-i386.iso* on a USB-Flash and see if I can duplicate the issue.

---

### Post by boof1988 on 2009-06-22
> **scales said:**
> ok well.  i definately am using the alternate disc, but i am booting off my usb.  i downloaded the jaunty-alternate.iso, and used unetbootin to get it onto my usb drive.  i definately am not able to install from offline though...wonder why...

When I used UNetBootin to *"put"* *ubuntu-9.04-alternate-i386.iso* on a USB-Flash, I get the same results as you have gotten.  The installation acts more like a *netboot* installation.  And then requires the network to complete the installation.

When I used "USB Startup Disk Creator" (in an existing 9.04 installation) to *"put"* *ubuntu-9.04-alternate-i386.iso* on a USB-Flash, the network was not needed to complete the installation.

So if you have the capability, you might try using the "USB Startup Disk Creator" (I think they are included in 8.10 and 9.04) to *"put"* *ubuntu-9.04-alternate-i386.iso* on a USB-Flash.

---

### Post by scales on 2009-06-22
ahh.  ok i think i may be able to do that.  thanks for your help :)

---

### Post by scales on 2009-06-22
Success! odd but unetbootin was the problem.  

Now, since you mentioned that you like to start from cli as well, what kind of setup do you use? gdm? wm? wicd vs network manager?

:)

---

### Post by boof1988 on 2009-06-23
> **scales said:**
> Success! odd but unetbootin was the problem.

Glad you got it working.  I looked around in the directories of the *UNetBootIn* setup of *ubuntu-9.04-alternate-i386.iso* and noticed a directory labelled "netboot" so that is what gave me an idea that (for some reason) the alternative installer is changing to a netboot installation.  There might be a way to modify the boot parameters and allow the installer to install without a network but that is advanced (to me) and beyond my skill level.

> **scales said:**
> Now, since you mentioned that you like to start from cli as well, what kind of setup do you use? gdm? wm? wicd vs network manager?

:)

I like to start with the Ubuntu 9.04 CLI installation and then add a window manager (or whatever it is called)...

```
sudo apt-get install lxde xinit
```

The LXDE seems to be pretty light (to me).

I don't usually use the minimal install on any wireless-networked computers so I don't usually have to worry about a wireless network manager.  Or actually what the installed network manager is doing since I usually install with the network cable plugged in.

I did use WICD for a short while for a WEP wireless-network Mythbuntu machine. But I was able to get the network to work with WPA (later on) without WICD so when I reinstalled I used the included drivers/manager for the wireless card instead of WICD.

I mostly just to a lot of fiddling... add stuff and try it out and then when the system is too confusing to me I re-install and start again.

For media playing... I like the terminal output that mplayer gives when playing music (either streaming or on HDD).  I can't remember which other player I tried (and liked).  Will have to try to find it again.

Glad you got it working.

---

