---
title: "Firewire External Harddrive Issue."
date: 2006-07-19
forum: Hardware &amp; Laptops
---

### Post by AnthoMacP on 2006-07-19
I recently decided i'd updated to 6.06 LTS after having used Breezy for a few months and I did it while on vacation. The installation went fine, and everything worked perfectly. I returned home and plugged in my 200Gb external media drive however and it failed to mount it. I plugged it in again, restarted and gave me a series of error messages to the tune of 
"cs: 10 port probe 0xa00xaff:clean
ieee1394 sbp2: aborting sbp2 command
0:0:0:0:
  command Inquiry 12 00 00 00 24 00
ieee1394 sbp2: reset request" etc. ending with some line about
"ieee1394 failed (-19)"

The drive still works perfectly on all my other computers (Ubuntu 5.10, Win2000, SUSE) and even on my XP boot on this computer. Can anyone tell me what exactly is wrong and how to possibly fix it? Thanks :)

---

### Post by Joeb on 2006-07-19
Try booting without the drive attached.  Then from the command line issue the following commands:

sudo rmmod ieee1394
sudo rmmod sbp2

plug the drive in and issue these commands

sudo insmod ieee1394
sudo insmod sbp2

and see if it mounts.

---

### Post by AnthoMacP on 2006-07-19
nope, when i type "sudo rmmod ieee1394" it gives me
"Error: Module ieee1394 is in use by sbp2, ochi1394"
"sudo rmmod sbp2" goes through fine

I tried the other two aswell just to see what would happen but nothing.

sudo insmod ieee1394 
insmod: can't read 'ieee1394'. No such file or directory
and same thing for sbp2

---

### Post by Loranga on 2006-07-19
I also have this problem, using a Sweex PCI firewire adapter and a Maxtor 300 GB drive. It works perfectly with USB2.

(Maybe a wild guess, but can it be a conflict with my PCMCIA PCI adapter card?)

---

### Post by Joeb on 2006-07-19
> **AnthoMacP said:**
> nope, when i type "sudo rmmod ieee1394" it gives me
"Error: Module ieee1394 is in use by sbp2, ochi1394"
"sudo rmmod sbp2" goes through fine

I tried the other two aswell just to see what would happen but nothing.

sudo insmod ieee1394 
insmod: can't read 'ieee1394'. No such file or directory
and same thing for sbp2

Oops, sorry about that.  I replied from work, which is not my Ubuntu box.  go back and do the rmmod commands again, but remove them in the order sbp2, ochi1394 and then ieee1394.  Then plug the drive in and insmod them in the opposite order (iee1394, ochi1394 sbp2) and see if you can mount.

I don't guarantee it will work, however, it does everytime I need to hook my ipod up via firewire.

---

### Post by AnthoMacP on 2006-07-19
> **Joeb said:**
> 
I don't guarantee it will work, however, it does everytime I need to hook my ipod up via firewire.

Naw it doesn't work either, and I'm not sure that that's what i'm looking for anyway, I was looking for more of a fix so that it works like it did back when i was running 5.10 where i didn't need to unplug it on boot and then plug it back in again and string a few commands before it worked. What is it about 6.06 that seems to be giving people trouble i wonder

---

### Post by Joeb on 2006-07-19
> **AnthoMacP said:**
> Naw it doesn't work either, and I'm not sure that that's what i'm looking for anyway, I was looking for more of a fix so that it works like it did back when i was running 5.10 where i didn't need to unplug it on boot and then plug it back in again and string a few commands before it worked. What is it about 6.06 that seems to be giving people trouble i wonder

Are you still getting the error when trying to do the insmod?  If so use the command modprobe instead of insmod.  As for why it doesn't work in the first place, that I don't know.  I have found with my ipod that it is intermittent.  Sometimes it works fine and others I have to issue the commands.  I imagine it has to do something with the hotplug or udev system (whichever one is in 6.06).

You might search on the Ubuntu site for firewire.  There are several other threads discussing similar problems to yours and they may shed light on how to fix your problem.

---

### Post by AnthoMacP on 2006-07-19
yes i've been watching them, from what i'm reading i get the feeling that maybe it's something just wrong with this version of ubuntu, maybe a patch is in order since there seems to be a few of us with the same issue all relating to firewire

---

### Post by Loranga on 2006-07-20
I can just confirm what AnthoMacP said, my firewire HD worked properly with Ubuntu 5.10, but not with 6.06.

---

### Post by AnthoMacP on 2006-07-20
Well hopefully someone comes up with a fix for this because I don't intend on moving back to 5.10 considering the improvements made in 6.06 but I also dont want to have a more a less useless partition on my computer until 7.x is released.

---

### Post by Joeb on 2006-07-20
> **AnthoMacP said:**
> Well hopefully someone comes up with a fix for this because I don't intend on moving back to 5.10 considering the improvements made in 6.06 but I also dont want to have a more a less useless partition on my computer until 7.x is released.


If you look at /proc/partitions with your firewire drive connected, do you see partitions listed for sda and sda1?  If so, do they exist under /dev?  If they are in the /proc/partitions but not under /dev, you could try the following commands:

sudo mknod /dev/sda b xx yy
sudo mknod /dev/sda1 b xx yy

where the xx and yy are the major and minor numbers listed for sda and sda1 under /proc/partitions.  That should get you the devices created so you can mount them.  However, it doesn't answer the question why they are not being created automatically.

You might also want to check out (maybe before doing the above) [https://wiki.ubuntu.com//DebuggingRemovableDevices](https://wiki.ubuntu.com//DebuggingRemovableDevices)

---

### Post by AnthoMacP on 2006-07-21
nope, they're not there. I'm fairly certain it's the reading of the firewire in general in ubuntu and not the harddrive because I also tested my friends DV cam and it gave me similar error msgs on startup but yet the firewire connection works perfectly in windows

---

### Post by autocrosser on 2006-07-21
I've ran into the same problem with my Firewire/USB2 drives--If I use USB2, they mount just fine--with Firewire, same problem you report....Sounds like a bug should be filed. I'm at work, so can't right now--but if you do, please post the bug# so we don't dual-post the problem.
 
As a interesting side note: My Firewire CD-RW works just fine--but now I can't use it to burn with--K3B has permission problems with it & not my internal burners--didn't have this problem in Breezy.

---

### Post by Joeb on 2006-07-21
> **AnthoMacP said:**
> nope, they're not there. I'm fairly certain it's the reading of the firewire in general in ubuntu and not the harddrive because I also tested my friends DV cam and it gave me similar error msgs on startup but yet the firewire connection works perfectly in windows

I'm I'm sorry that didn't work.  I was hoping it really would.  At this point I don't have clue as to what you should try next.  If you go to that link in the previous message, it gives instructions on how to post a bug report.  That would probably be the best thing at this point.  If you do report the bug, post the number here as autocrosser suggested and he can then go out to "confirm" it.

---

### Post by AnthoMacP on 2006-07-22
Bug was reported. [https://launchpad.net/distros/ubuntu/+bug/53746](https://launchpad.net/distros/ubuntu/+bug/53746) was that the site you had suggested? I couldn't find a link in your previous post but this was the first google response and it also recognized my Ubuntu Forums login and so I assumed it was.

---

### Post by autocrosser on 2006-07-22
That is exactly correct--I've posted an addition to the bug at Launchpad & I encourage everyone with this problem to goto the same post & add comment--If enough people add, the problem will be fixed faster.

---

### Post by Loranga on 2006-08-07
Any news regarding this? Can some money speed up the bug fix work?

---

### Post by AnthoMacP on 2006-08-13
Nope, no news yet. I've since had to rely on XP and i'm not at all impressed haha. Hopefully they'll get on it soon, I really don't want to have to wait till 6.10 to use ubuntu

---

### Post by chele on 2006-08-15
Doing the ' sudo modprobe ieee1394 ' & ' sudo modprobe ohci1394 ' did the trick for me, after rmmod'n them all.

---

### Post by Loranga on 2006-08-23
But it didn't do the trick for me. :(

---

### Post by gasoya on 2006-11-06
Has this issue already been resolved?

(I'm a total noob. Just installed 6.10, my first linux ever.)

My external hardrive is connected through a firewire pcmcia card. The drive is not mounted automatically when I plug it in. I can mount it manually, but when I do, I do not have permission to read the file contents of the drive unless I'm root.

I tried doing the whole chown thing as root but it just says the drive is "Read Only".

When I switch the harddrive to my USB2 inclosure everything works automatically.

Is this a seperate issue?

---

### Post by autocrosser on 2006-11-06
Yes-you are having the problem & no--I have not seen a resolve to the problem--I'm still using my external on USB2 also.....

---

