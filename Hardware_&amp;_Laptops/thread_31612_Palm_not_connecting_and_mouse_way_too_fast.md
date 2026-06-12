---
title: "Palm not connecting and mouse way too fast"
date: 2005-05-03
forum: Hardware &amp; Laptops
---

### Post by triskele on 2005-05-03
Well in my last distro I had to use Kpilot to sync with my palm T3 and it worked, until I tried to update it then it want kaput, now that I'm in GNOME I'd like to connect my palm via the cradle/cable connection. But it's not working I've tried all the port options in the gnome-pilot(i'm jsut assuming that's which one it is) setup and nothing will connect. I can hear my computer thinking when I push the Hot Sync button but that's as far as it goes.

My other problem is that my mouse moves way too fast and I have it on the lowest setting. Is there any way I can slow this thing down?

---

### Post by triskele on 2005-05-04
I'm bumping this. I read in gnome help that if it's a usb cradle (which it is) that there should be something in /dev/usb that I could use as a connection, but the only thing in there is "lp0" and that didn't work. I don't even know what that is. I really need somehelp here.

---

### Post by Bob D. on 2005-05-04
Here's a solution to get your Palm syncing. I just got this working with my Tungsten T. This information comes from the FedoraNews site: [http://fedoranews.org/tchung/gnome-pilot/]("http://fedoranews.org/tchung/gnome-pilot/")

 1. Create a /etc/udev/rules.d/10-local.rules file by typing in a terminal:

  sudo gedit /etc/udev/rules.d/10-local.rules

  2. In the Gedit document that opens, cut and paste the following text:

  KERNEL="ttyUSB1",SYMLINK="pilot"

  3. Save the document and exit Gedit.

  4. Create a symbolic link by cutting and pasting the following text into a terminal window:

  sudo ln -s /dev/ttyUSB1 /dev/pilot

  5. Reboot your system. (A step missing from the FedoraNews information and I think a critical step)

  6. Run the Pilot Config Wizard (Tools>Pilot Settings...) from Evolution.

  7. In the 'Device Settings' window, click the radio button for 'USB'. Leave the rest at their defaults.

  8. Configure your conduit settings as you wish.

  9. Press the HotSync button on your cradle. Your Palm should sync now.


 Now I have some issues when I have Backup enabled in the conduits on my system, but I think this is an issue just with my Palm. All the other items I want to sync (Tasks, Calendar, and Contacts) work great.


 Let us know what are the results when you get it configured.


 Bob


 p.s. I can't help you on the mouse. I haven't a clue as what to do, sorry.

---

### Post by triskele on 2005-05-04
Well after I did all that stuff you said and rebooted my computer I get a pleasant black screen. I can login from gdm blind but still nothing. Something's gotta be wong with X. I don't know what the command is to configure X(tried xconfig), because if I did I could start it in rescue mode and try that. If anyone can help, namely Bob D, I'd greatly appreciate it. Thanks

---

### Post by Bob D. on 2005-05-04
Wow, I'm so sorry to hear about the problem! :(

I'm at a complete loss as to what could have caused the problem. I posted exactly the same instructions I used to get my Palm to sync with Evolution. These instructions are the same ones I used to get Fedora Core 3 to sync with my Palm on a previous installation. Both FC3 and Hoary use udev, so I figured the way to get the sync working would be the same. As I said, I have my sync working fine using these instructions.

I really wish I had some sage advice for you, but I don't. I can't fathom how these instructions could have any effect on X. Hopefully a more knowledgeable user will jump in with some advice.

Bob

---

### Post by triskele on 2005-05-05
So do I, but there's always reinstalling ubuntu altogether. That of course is a last resort because then I'd lose som stuff I'd rather keep and have to reconfigure my music and video players all over again. Someone please help. I know it's a problem with X, but I don't know what the problem is or our to access X configuration from the command line in ubuntu.

---

### Post by praekon on 2005-05-09
I found a way to sync Palm Zire72 easily. Seems to be working also for Zire31 and Tungsten T5. If you want to try:
[http://www.ubuntuforums.org/showthread.php?t=31644](http://www.ubuntuforums.org/showthread.php?t=31644)

---

### Post by triskele on 2005-05-09
Well right now I'm just working on getting Ubuntu to boot to something other than a black screen, see my post in laptop help, but if I ever get Ubuntu working I'll be sure to check that out.

---

### Post by triskele on 2005-05-09
And for the record, Bob, it wasn't your fix that caused the problem I've since reinstalled twice and each time I reboot after a successful install I get a black screen. I've tried reconfiguring X but to no avail still the black screen.

---

### Post by spiderworm on 2005-06-30
This doesn't work with me, and I even have the same palm as you, the Tungsten T.  How can I troubleshoot this?

---

### Post by spiderworm on 2005-08-11
In order to get my palm to work, I increased the timeout from 2 to 5.  I don't know why, but in my case, that fixed the issue.

spiderworm

---

