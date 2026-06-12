---
title: "Give root password for maintenance (or type Control-D for normal startup):"
date: 2008-11-27
forum: General Help
---

### Post by NeoAndersen on 2008-11-27
Well, thats it...

After scan disk this message appears:
"Give root password for maintenance
(or type Control-D for normal startup):"
But my normal login don't work.

I must do manual fsck in maintenance mode and the root files system must be mounted in read-only mode.

The problem is duplicate blocks or something like that...

Please, help me!
I am not an expert in this kind of stuff...

: (

I have Ubuntu installed but some months later I installed Ubuntu Studio upon it...

Must I create an specific root password for maintenance in order to enter the maintenance shell?

How to do that  in a straight way as the error message just appears after the scan disk attempt in the startup?

---

### Post by NeoAndersen on 2009-01-20
Hello
I still need help with this problem. There are 2 months that I have to click on Esc to skip the scan disk that always start automatically on the start up...

Then I ask again:
How to create such root password for maintenance? 
How to do this scan disk manually?
Will this solve my problem?
What are the risks of lose data?

---

### Post by sisco311 on 2009-01-20
[list]

[*] back up your data
[*] boot a Live CD
[*] unmount the partition (if it's mounted):
```
sudo umount /dev/sdXY
```
replace /dev/sdXY with the partition(e.g. /dev/sda1).
[*] check the file system:
```
sudo e2fsck -C0 -p -f -v /dev/sdXY
```
[*]if that file system check finds something it can't fix automatically:
```
sudo e2fsck -f -y -v /dev/sdXY
```
[/list]

oh, you can do it with gparted(gui):
```
gksu gparted
```
select the *Check* option from the *Partition* menu.

---

### Post by NeoAndersen on 2009-02-02
Things become worse before I could try this solution... 
I was in a hurry to go out and I turn off the power of the computer before it have finished properly...

Now the problem is DRDY ERR
It can not start the X SERVER or GUI...
Then I can't run my Transmition, a torrent program, to see the clomplete downloads in order to backup... 
I have installed Ubuntu Studio over generic Ubuntu 8.04... Is it possible to start the other GUI I used before?

Other idea... I have 2 HD disks with 3 OS: Windows XP and Ubuntu in one HD and Ubuntu Studio in the other. Would it be possible and easier to solve the problem of Studio using the other Ubuntu? 

If your going to help me please put the solution steb by step because I know little about these things...

---

### Post by NeoAndersen on 2009-02-03
It seems my problem it's  not a easy one... I would be happy if someone tell me at least if it's possible to run Transmition without the GUI in order to me see the complete torrents in order to backup them...
If it's possible please send me the commands.

I would like to know how to run everything on Ubuntu whithout the X Server, just by using commands... How to learn it?

---

### Post by NeoAndersen on 2009-02-04
Hello!

Is it possible to tranfer all the torrents from the bad system to the good Ubuntu in the other HD and then install Transmition in order to continue downloading the incomplete torrents and see the complete ones to back up them?

How to make the new transmition recognise them?

---

### Post by NeoAndersen on 2009-02-07
Hello!

I entered these codes in the tty1 ( I didn't use the Live ubuntu cd):
-sudo umount /dev/sdb1
-sudo e2fsck -C0 -p -f -v /dev/sdb1
	
Then a bunch of white vertical stripes appeared on the screen. So I wait for about 5 hours to see what would happen... Then I type help and I figure out that with the command "sudo jobs ls -la" I would be able to see what the machine was doing. Then I wait for more 1 hour watching messages about errors, inodes, and nothing about fixing... Then I type this other command that the friend above suggest:
-sudo e2fsck -f -y -v /dev/sdb1

Then things began to happen in a different way... the words "fix? yes" was appearing in the screen... But I the end there was a error message remaining and there was a message asking for an advisable e2fsck... I tryed to do so but nothing happened this time...

After about 6 hours dealing with e2fsck I restarted the computer pressing the desktop button... But my Ubuntu Studio don't want to restart. This message is showed: "init: Error parsing configuration: No such file or directory"

	
But I could access my unfinished torrents through my other Ubuntu installed on the other hd.

Does this last error has a solution?

May it be because of the GUI problem?

---

