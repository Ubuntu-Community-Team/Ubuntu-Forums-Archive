---
title: "How to get eSata to work in Ubuntu 7.10?"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by fläsk on 2007-11-20
I have a Western Digital Mybook with eSata connection that I want to use with Ubuntu. I have previously used it with the USB-connection which worked well except that the drive wouldn't turn itself of when I shut down the computer. 

Now when I connect the drive with eSata Ubuntu won't find it. How do I solve this? It would also be nice if someone could tell me how to make it turn off itself when i shut down the computer!

I use NTFS since I'm also going to use it with another computer running XP. The card with the eSata connection is fully working and uses a sil3114 chip.

---

### Post by fläsk on 2007-11-21
It doesn't seem like Ubunut has found the drive. 

The WD-drives are my internals and the USB-drive a flash memory.

---

### Post by fläsk on 2007-11-27
So noone knows how to solve this problem? :(

---

### Post by Ralphie on 2007-11-28
i dont think its lookin very good for us, i too would like to utalize my esata external hdd.

here are two other unanswered threads:
[http://ubuntuforums.org/showthread.php?t=617020&highlight=esata](http://ubuntuforums.org/showthread.php?t=617020&highlight=esata)
[http://ubuntuforums.org/showthread.php?t=608912&highlight=esata](http://ubuntuforums.org/showthread.php?t=608912&highlight=esata)

we are all looking for the same thing :/ 

maybe there still needs to be a driver or application written for it... but i wouldnt know where to start on something like that.

if anyone can help, please do!

---

### Post by fläsk on 2007-11-29
It shoulnd't be too hard to write a driver for eSata since it's just only a s-ata with different connection. Probably it's just a matter of time until someone will do it..

Keep posting so we keep the thread alive untill someone posts a way to solve this!

---

### Post by Ralphie on 2007-11-29
I have been looking all over the net for info on esata and linux in general, the information is very scarce, and as far as I've seen, no questions are really answered. 

I think that someone said you can do it manually in fstab, but if it is not even getting recognized (in my case, it is not) I'm not really sure how to do even that.

It may be that the esata is just too new for linux? but it seems as the popularity is quickly growing, there should be a solution soon. keep those eyes peeled, and if anyone has a solution remember to let us know! :)

on a side note, I am not using a MyBook, I have an external case that i just stuck a brand new hdd in. but this is surely an esata problem and not a MyBook specific problem. 

Perhaps we should start a thread pertaining to esata specifically, or put it somewhere like the bug report thing for wanted features on the next release? i dont know how all that reporting stuff really works.

---

### Post by fläsk on 2007-11-29
Ubuntu won't recognize my disk either. 

I'll see if i can find a mod who can change the topic to a more accurate one.

---

### Post by Ralphie on 2007-11-29
I think that you can do that, when you click edit post, there is an option for something like "edit more" or something like that. I know I changed the title of one of my threads before.

If you search for esata in the ubuntu forums, there are a ton of people with this problem. in some cases there is a proposed solution, but never a reply on if it worked or not. 

When i get home i will try my hand at one of those proposed solutions and I WILL POST WEATHER OR NOT IT WORKED! :)

---

### Post by fläsk on 2007-11-29
I'll be looking forward to the report :)

In the meantime i'll be checking out the edit fuction.

---

### Post by fläsk on 2007-11-29
It seems lite I can only edit the title and not the topic.

---

### Post by fläsk on 2007-12-01
Well now we've got a new topic thanks to jdong :)

---

### Post by RRS on 2007-12-01
Here's what I have working:

Have a Sata drive that I'd previously used with an external USB connection.
I installed it into Kingwin Z1 enclosure which has eSata output but no adapter for the computer (was cheap).

Rather then spending $35+ on an eSata card/brackett I bought a Sata-eSata converter cable for $6.95 and routed it out the back of my case.

AS LONG AS I remember to turn the external drive  power on prior to the computer the system seems to see it as just another drive connected to the motherboard.

If I turn the power on after the computer the disc is seen but not auto-mounted. I can still click on it and select "mount" though.

Since I had formatted and written files to this drive thru USB prior to purchasing the enclosure this could explain why I don't seem to have a problem.

I'm sure there are other variables between how the device is connected to the motherboard; on-board eSata, add-on cards, etc.

Hopefully the explanation of my set-up will help someone with more expertise sort out some of the problems others are having.

---

### Post by fläsk on 2007-12-01
The strange thing is that my computer doesn't even find my external drive. I know the sil3114 card I'm using is working bicause my internal drives are connected through that card.

---

### Post by Ralphie on 2007-12-01
well as far as trying those other ideas out goes, i wasnt able to! my external enclosure turned out to be faulty. so i returned it to newegg, and since i really wanted to get some important files backed up quickly, i ended up driving out to the computer store, and buying the only case they really had, which was only USB. So ill no longer be able to work on the subject at hand! sorry guys :(

I can say that i was having problems with the drive somewhat because it was not yet formatted. also, before the case broke, (it used the sata to esata deal that you mentioned) if i turned it on before the computer started, ubuntu would hang up while loading, i never waited long enough to find out if it ever would make it in, but i sat there for a good 3 minutes and it never loaded up.

this oculd have been due to it not being formatted, or the faulty case, i couldnt really tell ya.  
but it sounds like RRS might be onto something more. 

good luck guys

---

### Post by RRS on 2007-12-01
An update with a bit more info.
I hadn't quite finished my coffee when I posted this morning so I later when back to refresh my memory.

As it turned out the disc was seen but not auto-mounted, didn't seem to matter when I turned the external power on either. I had to select "mount" from either the "Disk Mounter" panel applet or Places>Computer.

It's appearance in both places confirmed that both the bios and Ubuntu had no problem detecting the disc. Though I don't remember it earlier this week when I hooked things up I was asked for my password to mount the disc but it mounted correctly and I could read all my stored data when I opened it.

When I checked its properties from Places the size, make/model, etc. were correct but "permissions" stated "unknown" as owner. I think I had to "sudo chown....." originally but that must not've been a persistent change like with a removable USB device.

A bit of checking confirmed it was being mounted in mtab rather then fstab as I had thought,

Since I wanted auto-mounting with retained ownership/permissions I started editing. I got the UUID from properties and used it to create a new fstab entry. I also did another chown. To avoid a conflict between mtab and fstab I unmounted the drive before creating the fstab entry and the remounted to change ownership.

I rebooted with the enclosure power left on as a test and all seemed fine.

Unfortunately a reboot with the external disc turned off brought a new issue. Instead of continuing to a log in screen I got a console with messages about a failed disc check, creating a message log, etc., and dropping to a maintenance shell which was then teminated to a root terminal prompt. From this I rebooted and that got me to a login screen with a message about not being able to use my home partition. Selecting restart only kept me in the same circle.

During the reboot I noticed the bios only listed my internal drives, not the external.

I shutdown and then turned on the external drives power before starting the computer again. This time the bios splash screen showed all drives and the start up was normal with the external drive again auto-mounted in fstab with myself as the owner.

I'm guessing the boot problem is because I have the eSata connected thru an adapter cable directly to one of the motherboards sata ports. Being as it's a low cost board it probably doesn't have support for the "HotPlug" abilities that I would expect from a proper eSata port. The same behavior might be expected from an expansion bracket.

I've pretty much exceeded my Linux and hardware knowledge so if anyone can suggest a way to boot _without_ having my eSata drive connected and powered on each time I'd appreciate any input, as this does sorta' defeat the purpose of a portable device. :confused:

Sorry for such a long post but I didn't want to take a chance on leaving out anything that might be help full in sorting out the situation. I wonder if windows has any eSata issues.  :popcorn:

Added info:
Just tried booting with eSata cable unplugged from external drive in addition to power off. Same problem but I at least paid a bit more attention to the error message this time.
> Checking file systems......
fsck.ext3: unable to resolve UUID=(label of my eSata drive)
fsck died with exit status 8

---

### Post by fläsk on 2007-12-09
bump

---

### Post by fsando on 2007-12-13
I suppose Im having the same problem:
I have an esata expresscard, the card is:
Delock Express Card to eSATA II Nr. 61386

Is says on Delock's homepage that it should work under Linux. :)

I want to connect to an external drive via esata cable but the expresscard is not acknowledged at all Ubuntu never notices that the card is inserted. I'm not really sure what to do. I wrote support af Delock and got the unfortunate answer 

"No technical assistance support for Linux, Suse, Ubuntu .....
Too many different kernel and too many distributions":(:(:(

I'm trying to get a more useful answer from them.

---

### Post by fläsk on 2007-12-13
Lame excuses :|

---

### Post by holmes85 on 2007-12-19
i'm getting a really nice sony camcorder that can use eSATA do you think if i got a bracket for it from my sata2 to esata that and connected the camcorder it'll work? is it just hard drives or anything with eSATA? 

 this is the product
[http://www.newegg.com/Product/Product.aspx?Item=N82E16812226003](http://www.newegg.com/Product/Product.aspx?Item=N82E16812226003)

---

### Post by davescafe on 2007-12-25
Here is what I did to get eSATA working with Ubuntu 7.10:

**Please Note**
I am new at this, so please use these steps as ideas but do your own research so you are comfortable with what your are going to be changing on your machine. Most importantly, back up your important data before changing partition info.

_Enclosure_: Thermaltake Silver River Duo with eSATA from Newegg.

_Problem_: After I connected the eSATA enclosure to my computer it was not recognized by the OS (Ubuntu 7.10). External USB drives are recognized automatically by Ubuntu and mounted, but this does not happen with eSATA drives.

**Short Solution:**
Once the eSATA drive is recognized in the computer BIOS, getting it working in Ubuntu was the same as any internal SATA drive.

**Detailed Solution:**

_Part 1 – Set your BIOS so that the eSATA drive is recognized_:

I have an Award Bios - Yours may be a different brand with different steps.

[INDENT]1. Enter BIOS by pressing the <Delete> key on startup
2. Check to see what hard drives appear in the list. In my case, only my internal drives appeared. I did not see my newly-added eSATA drive.
3. Return to the BIOS main menu by hitting the <Esc> key
4. Select "Standard CMOS Features"
5. Select "Integrated Peripherals"
6. Go to "Onboard SATA/IDE Device" and set to "Enable"
7. I accepted the default setting for "Onboard SATA/IDE Ctrl Mode" which was "IDE"
8. Save your settings by pressing <F10> and selecting "Y"
9. Restart
10. Enter BIOS by pressing the <Delete> key on startup
11. Check to see whether the newly-added eSATA drive appears in the list. In my case, it now appears there.[/INDENT]

After this point, everything else is the same as adding a new internal hard drive to your Ubuntu system. If you are planning on installing Ubuntu, the next parts will be completed (mostly) automatically by the Ubuntu installation. Please proceed to the next parts to add your eSATA drive to your existing Ubuntu installation.

_Part 2 – Identify your eSATA drive device and UUID_:
I will assume that your eSATA drive is already formatted, and that the only thing you want to do is mount it. Naturally, you can create a new partition and format it, although I won’t included the steps for that here. Please see the link below, under “Sources” for more information on how to partition and format a new drive.

[INDENT]
1. Sign in to Ubuntu
2. Launch the Partition Editor
Please Note: The Partition Editor is NOT installed by default in Ubuntu 7.10, so if you have not installed it and you want to use it, here's how:
a) Go to the Gnome System menu and select Administration, and then "Synaptic Package Manager"
b) Install the package, "gparted"
c) When install is complete, you will be able to select the Partition Editor at: System >> Administration >> Partition Editor
3. The Partition Editor allows you to browse the different drives on my system by selecting the device drop-down in the upper right-hand corner. Browsing through the drives, I saw that my new drive appeared as /dev/sda1.
4. Now that I know the device designation, I need to find out the Unique ID (UUID). To get this, launch a Terminal window and type the following command:

> sudo vol_id -u /dev/sda1

IMPORTANT: You will want to substitute “sda1” with the device designation for your eSATA drive

This command will return a number that should be added to the Fstab file in Part 3 (below).[/INDENT]

_Part 3 – Create a Mount Point and Configure the Fstab File_

[INDENT]1. Create a mount point. I did this by creating a new directory in my home directory called “Vault”
2. Back up your Fstab file by opening a terminal window and typing:

> sudo cp /etc/fstab /etc/fstab.backup

3. Edit your Fstab file by typing the following into a terminal window:

> gksu gedit /etc/fstab

4. Add a line to fstab that will look something like this

For drives formatted in NTFS:

> UUID=D660D56760D54F3D /home/username/Vault     ntfs    defaults,umask=007,gid=46 0       1

For drives formatted in ext3:
> UUID=8c5452ff-dc76-44df-b887-d3245a847b6d /home/username/Vault     ext3 defaults 0       2



Note1: You will want to replace the example UUID number with with the actual UUID number for your device (see previous step)

Note2: You will want to replace “/home/username/Vault” with the path to the mount point you created on your computer.

5. Save the changes to fstab

6. Mount the new mount point
> sudo mount -a 

7. Grant permissions (assuming username is “username”)

> sudo chown -R username:username ~/Vault

> sudo chmod -R 755 ~/Vault

Note: you will want to substitute your actual username for “username” in the above commands
[/INDENT]

_Sources_
[INDENT]1. Adding new drive info: [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
2. UUID Info: [http://ralph.n3rds.net/index.php?/archives/175-Adding-a-new-partition-in-fstab-with-UUID.html](http://ralph.n3rds.net/index.php?/archives/175-Adding-a-new-partition-in-fstab-with-UUID.html)[/INDENT]

---

