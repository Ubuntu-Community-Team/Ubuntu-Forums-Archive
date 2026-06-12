---
title: "External drives and beyond"
date: 2009-09-27
forum: Hardware
---

### Post by texas.chef94 on 2009-09-27
[http://www.addictivetips.com/ubuntu-linux-tips/how-to-create-a-bootable-live-ubuntu-904-usb-drive/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-create-a-bootable-live-ubuntu-904-usb-drive/)

is a URL dedicated to installation of Ubuntu 9.04 to USB. It speaks about a tool to ease installation
/home/allen/unetbootin-linux-372 which as you see is in home.
I have not gotten deep into the process, but already I have a concen. I attempt to open said tool and get
Couldn't display "/home/allen/unetbootin-linux-372".
So before I get any deeper in this operation can someone shed light on my inability to open  Is this a mount or ownership issue surely not. Please advise and as always thank you for advancing my Linux learning curve.
While I am at it please look at the attachment the Data1 partition is a mounted device I use for data. That second one I merely made ext3 and the remainder was automatic I guess assuming my intention is to create a 2nd data disk. At any rate it is not mounted and my vision is this is where 9.04 will eventually reside.
Please address any configuration, mounting etc in detail so even an old man can understand. Have a great Sunday and thanks as always.

---

### Post by QLee on 2009-10-24
[QUOTE=texas.chef94][http://www.addictivetips.com/ubuntu-linux-tips/how-to-create-a-bootable-live-ubuntu-904-usb-drive/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-create-a-bootable-live-ubuntu-904-usb-drive/)

is a URL dedicated to installation of Ubuntu 9.04 to USB. It speaks about a tool to ease installation
/home/allen/unetbootin-linux-372 which as you see is in home.
I have not gotten deep into the process, but already I have a concen. I attempt to open said tool and get
Couldn't display "/home/allen/unetbootin-linux-372".
So before I get any deeper in this operation can someone shed light on my inability to open  Is this a mount or ownership issue surely not. Please advise and as always thank you for advancing my Linux learning curve.
While I am at it please look at the attachment the Data1 partition is a mounted device I use for data. That second one I merely made ext3 and the remainder was automatic I guess assuming my intention is to create a 2nd data disk. At any rate it is not mounted and my vision is this is where 9.04 will eventually reside.
Please address any configuration, mounting etc in detail so even an old man can understand. Have a great Sunday and thanks as always.[/QUOTE]

It's my opinion that it is acceptable to "bump" a post after 24 hours with no answer if the team that follows up on no reply posts misses your question.

I see on the sourceforge page for unetbootin-linux:

"If using Linux, make the file executable (using either the command chmod +x ./unetbootin-linux, or going to Properties->Permissions and checking "Execute"), then start the application, you will be prompted for your password to grant the application administrative rights, then the main dialog will appear, where you select a distribution and install target (USB Drive or Hard Disk), then reboot when prompted."

Did you make the file executable as it suggests? 

That file is a binary, it won't do you any good to try and read it with a text reader.

I don't know anything about unetbootin-linux so I can't help any further with it or recommend it. The sourceforge site for the program has a FAQ, it might help you.

---

