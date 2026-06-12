---
title: "iphone firmware 2.x support now in ubuntu"
date: 2009-01-19
forum: Hardware
---

### Post by sudo panda on 2009-01-19
EDIT: This method only works through WiFi.

This post is purely for anyone out there like me, who has had such a headache trying to find a work around for ubuntu's (or should i say apple's) lack of support for the iphone with the newest firmware 2.x (that being 2.1 or 2.2) in linux.

I found [this post]("http://marcansoft.com/blog/2009/01/using-amarok-and-other-itunesdb-compatible-software-with-the-iphone-2x/") particularly useful in figuring out a proper work around for it.

Basicly, changing a **4** to a **2** in **/System/Library/Lockdown/Checkpoint.xml** (you'll have to shh into the iphone in order to get it)
and copying the file onto your desktop, change the value under **DBVersion** then replacing the old Checkpoint.xml with the new one (MAKE SURE TO DO A BACKUP FIRST) will allow you to sync with amarok or any other iphone supported media player.

Hope this helps someone in need :popcorn:

---

### Post by igknighted on 2009-01-19
> **sudo panda said:**
> This post is purely for anyone out there like me, who has had such a headache trying to find a work around for ubuntu's (or should i say apple's) lack of support for the iphone with the newest firmware 2.x (that being 2.1 or 2.2) in linux.

I found [this post]("http://marcansoft.com/blog/2009/01/using-amarok-and-other-itunesdb-compatible-software-with-the-iphone-2x/") particularly useful in figuring out a proper work around for it.

Basicly, changing a **4** to a **2** in **/System/Library/Lockdown/Checkpoint.xml** (you'll have to shh into the iphone in order to get it)
and copying the file onto your desktop, change the value under **DBVersion** then replacing the old Checkpoint.xml with the new one (MAKE SURE TO DO A BACKUP FIRST) will allow you to sync with amarok or any other iphone supported media player.

Hope this helps someone in need :popcorn:

Does it need to be jailbroken to do this?

---

### Post by sudo panda on 2009-01-19
yes, in order to ssh into the phone you need to have **BSD Subsystem** and **OpenSSH** installed through Cydia. (a package acquired through the jail breaking process) :)

---

### Post by sleepercivic88 on 2009-01-25
I edited the xml file on the Ipod and restarted it.....it still mounts as a camera and I cant get gtkpod to see it correctly.  What should I do.  Did I miss something.

Thanks

---

### Post by sudo panda on 2009-01-25
ahh, your mounting your iphone/ipod touch through usb.

Unfortunetly, this method only works with mounting the ipod touch or iphone via wifi. :eek:
using the usb chord to connect the device will still make it show up as a camera sorry ;)

If you want more infomation about mounting the device through wifi you can find detailed instructions [at this link]("https://help.ubuntu.com/community/PortableDevices/iPhone"). All you have to do is follow the "Syncing Music on Firmware Versions 1.x" as the altered XML file will now support this method.

---

### Post by Boomhauer on 2009-01-29
thank you for this post!  ive been confused on how to edit the Checkpoint.xml.  ive been trying to mount via usb, didnt know about the ssh.  thanks again!
EDIT: alright ive got ssh setup and can get in but i cant seem to /System!  if i ssh as root i have ```
huff:~ root# ls
Library/  Media/
huff:~ root# cd Library/
huff:~/Library root# ls
AddressBook/  Caches/  Cookies/  Keyboard/  Lockdown/  Preferences/
huff:~/Library root# cd Lockdown/    
huff:~/Library/Lockdown root# ls
activation_records/  device_private_key.pem  pair_records/
data_ark.plist       device_public_key.pem

``` and with mobile i get ```
huff:~ mobile$ ls
Applications/  Library/  Media/
huff:~ mobile$ cd Library/
huff:~/Library mobile$ ls
AddressBook/             Keyboard/                 SMS/
Application\ Support/    LockBackground.jpg        Safari/
Caches/                  Logs/                     Stocks/
Calendar/                Mail/                     Voicemail/
CallHistory/             Maps/                     Weather/
Carrier\ Bundle.bundle@  MobilePhone/              WebClips/
ConfigurationProfiles/   Notes/                    WebKit/
Cookies/                 Operator\ Bundle.bundle@  YouTube/
DataAccess/              Preferences/

```
no system anywhere
EDIT2:  i am an idiot!  i dont know why i didnt try this from the get go, but cd /System took me to where i need to be :)

---

### Post by sudo panda on 2009-02-04
Haha, glad you worked it out :) 
After replacing that file all should be smooth sailing ;)

---

### Post by doublepedaldylan on 2009-04-30
It is not letting me edit the .xml file.  I even copied to desktop and edited that one, but I could not copy back.  I do not have permission it seems...

What gives?

Anyone know?

---

### Post by gamelover25 on 2009-11-11
> **doublepedaldylan said:**
> It is not letting me edit the .xml file.  I even copied to desktop and edited that one, but I could not copy back.  I do not have permission it seems...

What gives?

Anyone know?

I'm having the same problem, I know this is old, but can someone please help me

---

### Post by sudo panda on 2009-11-11
im really not sure... i haven't really played around much with the iphone for a very long time... im on software 3.0 now and this method is redundant for me now, so its very hard for me to test it..

but the only thing i can suggest is to check your permissions as it should be a very simple process of dragging and dropping the file over the top of the old checkpoint.xml

does it give you an error at all?
something that may point you to the reason for the error?

---

### Post by sudo panda on 2009-12-01
I've recently posted a thread on making iphone work with ubuntu when you've got the 3.0 and 3.1 software.
Would anyone like a how-to?

---

