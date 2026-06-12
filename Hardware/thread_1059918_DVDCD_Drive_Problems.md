---
title: "DVD/CD Drive Problems"
date: 2009-02-04
forum: Hardware
---

### Post by levelfivevegan on 2009-02-04
Hey there, This is my first post here so sorry if this is in the wrong section. I have 2 disk drives in my computer, A CD-ROM drive and a CD/DVD-ROM drive. If I click 'Places' in ubuntu both of these come up as clickable options. However, I am unable to click on them and view there contents whether a disk is in the drive or not. DVD's seem to load up and the loading light flashes as normal but nothing happens on the screen. 

Both of these drives were working fine on Windows XP so I think its a software problem not a hardware problem. 

You'll be pleased to know that i have no idea what make/model the drives are so i'm sure that will help alot!

I get this message when I try to view them

"DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

And also

"Unable to mount media.There is probably no media in the drive."

---

### Post by 7mkgw7q on 2009-02-04
Ok, we might be able to get to the bottom of this. I want you to look at a couple of things. If you can't figure anything out, either paste the output here or send it to me and I will look through it. Type dmesg and see if anything jumps out at you. If not, try looking through /var/log/messages and do the same. If nothing is obvious there, take a look at /var/log/syslog. If you see nothing in any of these, you can, as I said, post the output here or send it to me. Either way is fine. We will see if we can get to the bottom of this.

---

