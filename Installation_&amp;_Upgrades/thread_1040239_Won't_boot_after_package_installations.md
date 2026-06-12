---
title: "Won't boot after package installations"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by pib712 on 2009-01-15
Firstly, sorry if this has been posted before - or if anyone feels this is the wrong section for this question.

The other day I installed a few packages for Intrepid, and I haven't managed to get it to boot since. I've tried recovery mode, but whatever I do, booting just hangs just before showing the desktop (the screen turns beige for a second as if the desktop's about to come up, but then refuses to go any further - I just get the "busy" cursor).

I don't really remember all the packages I installed, but I think glib and gobject were two of them, as well as some Canonical fonts. I'm not sure if they all installed fully or properly. I'm assuming that this is the reason it won't boot.

Right now I'm running Intrepid off a Live USB, which works fine. I don't know how to use the package manager or terminal to remove packages from the hard drive. Is there any way to find out what the packages were and remove them, or find out what else might be causing the problem?

Thanks in advance.

---

### Post by zwygart on 2009-01-15
Are you able to go to virtual terminal?

After boot up press CTRL+ALT+F1. This will bring you to a shell. Login and run this command : sudo apt-get install -f
This may repair your system or at least say what is wrong.
Post any problem. 
If you are not able to switch VT, then you may try to chroot from your live USB. But I will tell you how to do if it does not work.

---

### Post by fenario on 2009-01-15
Hi pib

I can't help with your problem but answer some of the questions:

you can find the installed packages in:

places > computer > filesystem > /var/cache/apt/archives
you may recognize the apps and libs you installed
it may be a good idea to copy those debs and use them again in a reinstall
or for friends so you don't need to go on the net to get them .
I always save mine and keep them all on a big flash drive....you never know when you need them again.

then remembering what they were you open synaptic

in synaptic package manager all installed files are green in the first column (S)
right click on a green file and you see: mark for removal, tick that
and follow the prompts

if things get stuck with synaptics open terminal and enter:
**sudo apt-get install -f**
it will give you the choice to remove files; answer yes (Y)

but all this works only if you are already inside the OS

in synaptic, in the tabs at the bottom concerning a deb file see tab: Installed Files: it shows what files are installed.............but the list of installed files is only available for installed packages 

it looks like you're snookered and you may have to reinstall the system.....groan

just wait and see for more replies first, mate.

---

### Post by pib712 on 2009-01-15
Hi, thanks for both of your replies. When I run sudo apt-get install -f, it comes up with no software installed at all, but I assume that's because I'm still running off the Live USB rather than the installation on the hard drive. If that's the case, how can I find the software on that installation when I can't even boot into it? I looked for packages in the directory fenario suggested but there's nothing there of any use (an empty text file called "lock" and an empty folder called "partial"), and Synaptic only shows the default packages found on the USB - not the ones on my actual installation. Thanks for your suggestions anyway. I think I'll just grab any important files and reinstall the whole thing...probably the simplest solution ;)

edit: Changed root to hard drive like zwygart suggested - we could be onto something here :D I'll try playing with this a little longer...

---

