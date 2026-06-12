---
title: "Installation Problems for Jaunty"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by crushingandy on 2009-10-16
I'm trying to install Jaunty Jackalope on my external hdd, but when I get to the part where it tells me to select my disk, my external hdd isnt there. And yes, my harddrive is on and plugged in.

---

### Post by phillw on 2009-10-16
> **crushingandy said:**
> I'm trying to install Jaunty Jackalope on my external hdd, but when I get to the part where it tells me to select my disk, my external hdd isnt there. And yes, my harddrive is on and plugged in.


Crikey ... 1st post .... what a question !!!!!


1st up - is the drive a usb drive, or fire-wire drive - Modern computers can boot from usb devices, but not from, as far as i know, fire-wire ones.
Assuming it to be a usb drive ....

Then .....

[http://books.google.co.uk/books?id=HZ37FT3unW8C&pg=PA39&lpg=PA39&dq=install+ubuntu+on+removable+hard-drive&source=bl&ots=A1gWBYcZ46&sig=01ChTdCfuCZFUEyIwcJcBkoOiXo&hl=en&ei=J7vYSsSTFYeL4Qbruvn6CA&sa=X&oi=book_result&ct=result&resnum=7&ved=0CBwQ6AEwBg#v=onepage&q=install%20ubuntu%20on%20removable%20hard-drive&f=false](http://books.google.co.uk/books?id=HZ37FT3unW8C&pg=PA39&lpg=PA39&dq=install+ubuntu+on+removable+hard-drive&source=bl&ots=A1gWBYcZ46&sig=01ChTdCfuCZFUEyIwcJcBkoOiXo&hl=en&ei=J7vYSsSTFYeL4Qbruvn6CA&sa=X&oi=book_result&ct=result&resnum=7&ved=0CBwQ6AEwBg#v=onepage&q=install%20ubuntu%20on%20removable%20hard-drive&f=false)

I *think *that you *may* be able to follow the rules as per installing on to a usb pen-drive in persistant mode. As your machine is windows, this may be what you're looking for....

[http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/)

I'd love to hear how you get on with it.

Regards,

Phill.

---

### Post by crushingandy on 2009-10-16
How come when I install Karmic, it works fine without doing anything special, but when its jaunty, it wont show up?

---

### Post by phillw on 2009-10-16
I'm sorry, you'll have to let s.o. else answer  that one - I currently only have one computer and it's needed for my work. (My Spare has been pressed into service)

I'm looking forward to switching over to 9.10 at some point, but I run a full LAMP installation and mail / web server..

I'm not quite ready to risk messing it all up - I'll most probably await the next LTS version of ubuntu.

Soz I couldn't be of more help :(

Phill.

---

### Post by crushingandy on 2009-10-16
So when I finally get this done, will I be able to update and download new programs like normally?

---

### Post by phillw on 2009-10-16
I'd wait for some one to confirm that you can use persistant mode for a usb hard-drive, whilst there is no reason for you not to be able to do so - there may well be a better way.

That is why I suggested the link specifically for a usb hard-drive - as it seemed closer to what you want - i.e. a full ubuntu install, on a hard-drive.

The secret to these sorts of things is to pop the question on and ...... wait a while..... It's amazing how someone else will have done what you want to do - and be happy to tell you the pit falls.

Installing onto a pen drive in persistant mode is not un-common, I'm just unsure if there would be a slightly different set of 'rules' for a full blown install on a usb hard-drive..

From reading the article on the hard-drive installation - I believe you DO get a full-blown installation capable of updates, etc.

I also noted that it mentions the use of fire-wire drives - it has certainly caused my eye-brows to raise..... I have a fire-wire hard drive kicking around ...

Phill.

---

### Post by crushingandy on 2009-10-16
Okay, I have decided to skip with the Jaunty, and I have Karmic Koala on. Im using it right now, but the reason I wanted to downgrade was because whenever I try to update, it fails and I cannot boot anymore. To tell the truth, I dont even know how to update. Any suggestions?

---

### Post by tpjk on 2009-10-16
> **crushingandy said:**
> Okay, I have decided to skip with the Jaunty, and I have Karmic Koala on. Im using it right now, but the reason I wanted to downgrade was because whenever I try to update, it fails and I cannot boot anymore. To tell the truth, I dont even know how to update. Any suggestions?

usually, if there are updates available for any of your installed programs ubuntu will notify you - i'm not sure if the regular updating process has been changed since jaunty but usually the taskbar on top will display an icon that you have to double click in order to get a list of the updates that are available and start the actual update. if you want to update manually just open up a terminal and type

```
sudo apt-get update
```

followed by

```
sudo apt-get upgrade
```

hope this helps.
cheers!

---

