---
title: "Installing A Printer - There is hope!"
date: 2015-06-07
forum: Hardware
---

### Post by delta410 on 2015-06-07
I recently tried to reinstall my H-P Laserjet 4 laser printer after a clean reinstallation of Ubuntu. Here's the short version:

1) I tried installing the printer (connected and powered up) using the "Printers" function on the "System Settings" panel. The machine failed to auto-detect the printer, and I was not offered a way to install it manually. Also, some dependency messages flashed on the screen while the detection process was happening.

2) I went to the command line and ran "sudo hp-setup -i". Again, the machine failed to auto-detect the printer, which was powered up and connected.

3) Downloaded and installed the HPLIP Toolkit. Same problem - machine failed to auto-detect the printer, and I couldn't continue manually.

My printer and my computer worked swimmingly well together until a few weeks ago when I picked up a virus (yes, Linux viruses do exist), and had to back up my data (using Knoppix) and do a clean re-install of Ubuntu Linux.

I also have a Windows 7 machine. Installing the printer on ***that*** machine was a breeze. I was up and running within minutes. (I share the printer with my Windows and Linux machines via a manual switch box - yes, it was set correctly).

As I was about to give up (the original reason why I was composing this posting), I clicked on the "power" icon in the upper-right hand corner of my screen (I'm using Gnome classic). I was trying to get the version number of the Ubuntu Linux distro I was using (12.04 LTS), when I noticed a line in the drop-down menu which said "Printers". On a whim, I clicked on it. It walked me through a manual, step-by-step installation. In a few minutes, I was pulling a freshly-printed test page out of the printer's document hopper.

Now, I wonder why the "printers" function in the System Settings control panel couldn't have made it this easy for me to get my printer going. 

Anyway, for those of you who are going crazy trying to install a printer "automatically", there is hope!

Oh, yes, I have the ClamAV daemon running on every startup. I'm also considering installing AVG Antivirus for Linux. One cannot be too careful these days!

---

### Post by tgalati4 on 2015-06-07
What was the virus that you encountered in Linux?  What was the hardware switch device?  Is this a bi-directional parallel port printer switcher?

---

### Post by delta410 on 2015-06-07
> **tgalati4 said:**
> What was the virus that you encountered in Linux?  What was the hardware switch device?  Is this a bi-directional parallel port printer switcher?

No idea what the virus was. All I know is that when I made the mistake of clicking on a link in a "Suggested Post" on Facebook, all of a sudden my computer ran V-E-R-Y slowly and erratically. That was a *big* red flag to me!

The switchbox is, AFAIK, a simple parallel port switchbox for sharing a printer with 2 computers. Got it at a thrift shop some time ago. Not sure if it's bi-directional. Parallel ports don't lend themselves to auto-discovery like USB ports do anyway, again AFAIK. This is why a manual installation option is so important.

---

### Post by kurt18947 on 2015-06-08
I have a suggestion for other readers here - delta410 has solved his/her problem. The 'printers' app in Ubuntu-Gnome is pretty limited. There is available in the repositories something called "system-config-printer". It is the printer admin app found in pre-gnome 3 versions and still found in Xubuntu (and likely other distros). It is launched via alt-F2 or via the command line. I created a desktop launcher. 'system-config-printer' offers far more information and options than the default gnome 'printers' app.

---

### Post by tgalati4 on 2015-06-08
The parallel switch box will interfere with auto-detection of the printer.  I had a couple that I got rid of years ago.  Next time, plug the printer in directly, set up the printer (it should auto-detect), run a test page, print a test document.  Then unplug the printer and plug it into the switch box and try printing through the switch box.  

But yes, as kurt18947 pointed out, there are several ways to install a printer.  The newer print installation methods expect a modern (USB or network) printer.  Those with older printers and gear (such as a parallel switch box) will have to get creative.

---

