---
title: "All access needed"
date: 2005-12-01
forum: General Help
---

### Post by Fittersman on 2005-12-01
ok this is the deal, i want all access to every nook and cranny on my computer, windows partitions, all of it but how?

---

### Post by Bachstelze on 2005-12-01
run "sudo fdisk -l" in a terminal and post the reply here. btw, did you get your modem working ?

---

### Post by RAOF on 2005-12-01
For accessing your windows partitions, check this [wiki page]("https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28windows%29").

---

### Post by Fittersman on 2005-12-02
no my modems still not working i have a question for ya though. When you run scanmodem does it create a folder called modem?  and if it does what do i do with it?

---

### Post by aysiu on 2005-12-02
[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows) is also handy

---

### Post by Bachstelze on 2005-12-02
[QUOTE=Fittersman]no my modems still not working i have a question for ya though. When you run scanmodem does it create a folder called modem?  and if it does what do i do with it?[/QUOTE]

Yes it does. What you can do is posting the contents of your modemdata.txt file here and I'll see if I can help you :)

---

### Post by Fittersman on 2005-12-04
aw man then id have to type it all out and stuff, any easier way than that?

---

### Post by soulestream on 2005-12-04
> aw man then id have to type it all out and stuff, any easier way than that?

PLease, Please say you are joking. 

you could copy and paste it

or 

you could use a pastebin website

soule

---

### Post by aysiu on 2005-12-04
In the off-chance that you're not joking, maybe Mepis would be up your alley. It puts all your hard drives and partitions on the desktop and when you click them, they automount and open right away--no configuring.

By the way, yes, you can copy and paste, and if you really think it's that big a deal to type out "all that stuff," do you realize how much people have typed here already trying to help you?

---

### Post by Fittersman on 2005-12-05
alright ill get it for you then when i get home because im at school right now.

---

### Post by Fittersman on 2005-12-05
ok i changed my mind when i saw the amount of typing id have to do so i guess im guna need some help getting my authorities up because i cant even write to a floppy, i need all access to everything its making me mad i think i might just stick to windows! (you dont want that so you will help me :) )(i hope) but anyway im not guna write that out so if i could get it onto a floppy i could take it to windows to give to you so i need to be able to do anything with ubuntu, i know that password it always asks you so ya (i dont know if i explained that well or not)

---

### Post by soulestream on 2005-12-05
> i think i might just stick to windows! (you dont want that so you will help me

actually no. Windows is a good operatiing system. Pick up a free copy of AVG antivirus, get M$ anitspyware beta, and find a copy of Partition Magic. You can use partitiion magic to remove the linux partitions and set everthing back to NTFS, that way you can get stuff done. You may want to pick up a typing tutor program or open Word and use the help feature to search for "copy and paste"


soule

---

### Post by Bachstelze on 2005-12-05
[QUOTE=soulestream]actually no. Windows is a good operatiing system. Pick up a free copy of AVG antivirus, get M$ anitspyware beta, and find a copy of Partition Magic. You can use partitiion magic to remove the linux partitions and set everthing back to NTFS, that way you can get stuff done. You may want to pick up a typing tutor program or open Word and use the help feature to search for "copy and paste"[/QUOTE]

That was briliant :lol:

---

### Post by Fittersman on 2005-12-06
hey you guys are supposed to be all for linux so you do not want me goin back to windows so you will help me...

---

### Post by soulestream on 2005-12-06
it kind of like being in a club. 

You have two people.

Person #1. Wants to be in your club, is willing to read, take time to help us, help them and have some common sense. 

Person #2 Wants everyone to do things for them, is lazy, and probably has trouble not walking into walls on a daily basis.

Person #1 is welcome in the club. Person #2 can go climb a tree in Redmond.


soule

---

### Post by Fittersman on 2005-12-06
ok lets get back to the problem whatever it was :D alright?

---

### Post by Bachstelze on 2005-12-06
And what exactly is the problem ?

---

### Post by Fittersman on 2005-12-06
something about me having permissions problems

---

### Post by Bachstelze on 2005-12-06
If it's about your floppy disk I cannot help you, I have a laptop with no floppy drive.

---

### Post by Fittersman on 2005-12-06
ok this is the problem.

i can mount all the stuff i need it works. I cannot write to it though (now im talkin about my windows partition) i used the recovery console from the grub loader and it tells me that i cant change "ownership" of the device from root to me because it is a read only file. Ya basically i want a quick fix to be able to write to everthing and allow all users to do so but i want a quick way if possable but if i have to manually change all of them by hand (if i can get it to work that way) i will. (by all of them i mean like floppy drive, hda1,hda2,hda3 and so on)


o ya and i need to get my MP3 player to work on ubuntu also so then hymntolife i can get you the other files from ubuntu to windows to internet so you can help me :D

---

### Post by Bachstelze on 2005-12-06
If you're talking about NTFS partition, it's better this way. If you try to write on it, the risk of losing the entire partition is quite high.

---

### Post by Fittersman on 2005-12-07
i dont really need to write to it all i want to do is have it owned my me not rooot so i can at least view and execute the files.

---

### Post by Bachstelze on 2005-12-07
If I'm not mistaken, you can view/execute the files even if they're owned by root. That's the way it worked for me, at least...

---

### Post by Fittersman on 2005-12-07
nope i went into properties and the permissions tab and it says only the owner can access the files and execute them (i used recovery console to get to them and i tried changing ownership but it says that since it is read only file i cant) everyone else cant do anthing with it so i just want to change ownership to me not root.

---

### Post by RAOF on 2005-12-07
Well, you cant change file permissions on windows drives (NTFS has file permissions, but we don't have write support, FAT doesn't even have any permission mechanism).  However, if you've followed the instructions on the [wiki page]("https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions"), you should have read access to the drive.  If you want execute privileges, I think you need to change the "fmask=0111" to "fmask=0000" in the instructions.

---

### Post by soulestream on 2005-12-07
fmask =777 is all access

soule

---

### Post by RAOF on 2005-12-07
Actually, I think that fmask=777 is **no** access.  For no obvious reason, the fmask specifies what permissions **not** to give, so 777 translates to: do not give anyone read, write, or execute access.

---

### Post by Fittersman on 2005-12-07
where do i change that

---

### Post by syncme on 2005-12-07
I'm not sure if this is what you are looking for.....

If you just want to login as root here it is:

sudo passwd root

Set your password for root

In the menu go to "System"  > "Administration" > "Login Screen Setup"

go to "Security" tab and under "Options" CHECK  "Allow root to login with GDM"

then logout and login as root.

Juts a warning this will give you access to places that you can break your system. I don't recommend it.

Syncme

---

### Post by soulestream on 2005-12-07
fmask = 777 is all access
umask = 777 is no access


soule

---

### Post by Fittersman on 2005-12-07
i am lost with this umask and fmask i went to etc/fstab and i was there and i had no idea what to do when i got there, i read the wiki page (not for beginners) so if you could tell me where to add these fmasks and umasks and stuff it would be great

---

### Post by soulestream on 2005-12-07
1. Open terminal

2. in terminal type  less /etc/fstab

3. select the text and right click (copy)

4. paste it in here

we can then tell you exactly what to change

soule

---

### Post by Bachstelze on 2005-12-07
@Fittersman > I told you exactly what to change in the other thread (or maybe it was inn this one :/)


Now Playing : Stratovarius - Lead Us Into The Light

---

### Post by RAOF on 2005-12-07
Alternatively, try the automatic-for-beginners part at the top of the wiki page.  A quick summary:
[LIST]
[*]Open a terminal
[*]type (or copy) the following commands into the terminal window:
```
wget http://www.ubuntulinux.nl/files/winmac_fstab
chmod u+x winmac_fstab
sudo ./winmac_fstab
```
[/LIST]
The sudo step will ask for a password.  Type your own password in.  There will be no feedback (*s) while you are typing your password in.  This is normal.

You should now have access to all your partitions, mounted in various folders under the /media directory.

---

### Post by Fittersman on 2005-12-07
lol sorry hymntolife

and i dont have a modem hooked up yet so that simple way wont work

and soulstream i cant copy and paste because i am going from windows to use the internet back to ubuntu to use it my windows partition is nfts or something not fat32 its options are defaults and there are two 0 at the end

---

### Post by RAOF on 2005-12-07
Ok, then the not so easy way... :)

You have, somewhere in your fstab, a line that looks like this:
```

/dev/hda2        /media/Windows   ntfs   defaults     0       0

```
(except the first bit - /dev/hda2 will probably be different but similar, and the second part - /media/Windows will also be different, but similar)?

What you want to do is to change the "defaults" bit.  In order to do that, you'll need to edit the file.  Type "sudo gedit /etc/fstab" from a terminal window, and you should be able to edit the fstab file.

Now, replace "defaults" in that line with "ro,auto,fmask=0111,dmask=0000".  Save the file.  Next time you reboot, you should be able to read from your windows partition.  (There is a way to do this without rebooting, but it's just simpler to reboot).

---

### Post by soulestream on 2005-12-07
First make sure you are umounting the remounting the filesystem after you make changes. they wont take effect until then

Second this is my /etc/fstab

/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda1       /media/windows  ntfs    ro,noauto,umask=022  0   0
/dev/sda2      /media/shared   vfat   rw,auto,umask=000   0    0

As the above post suggests you will have different /dev/*** than i will. just look for ntfs for your windows drive (if its ntfs) or vfat for your fat32. the umask=000 gives full access to the drive. umask =022 gives read and execute access to the drive. 

noauto - will mean you have to mount the drive
auto means it mounts at boot up
you can also add "user" is you want a user to be able to mount it.

roaf's post will give you no access to directory and execute only access to the files.
If you want use dmask , fmask it will be 0777 for all access , 0555 for read and execute.

soule

---

### Post by RAOF on 2005-12-07
[QUOTE=soulestream]...
roaf's post will give you no access to directory and execute only access to the files.
If you want use dmask , fmask it will be 0777 for all access , 0555 for read and execute.
...[/QUOTE]
I have just tested this.  fmask=0777 gives you **no access**.  fmask=0111 gives you **read** (and write, if not NTFS) **access**.  fmask=0000 gives you **full access** read, write (again, if not ntfs), execute.

---

### Post by soulestream on 2005-12-07
> I have just tested this. fmask=0777 gives you no access. fmask=0111 gives you read (and write, if not NTFS) access. fmask=0000 gives you full access read, write (again, if not ntfs), execute.

I concede. kind of. :D 

after some googling, 

fmask=000 is all access in vfat
fmask=000 is no access in smbfs

im not exactly sure why they are different, but they are. I never use fmask, dmask on anything other that samba shares, so that was the confusion. fmask, dmask wasnt added until 2.6 kernel and has no man entry for some reason. 

with apologies, kind of. :p 

soule

---

### Post by RAOF on 2005-12-07
Ok.  I didn't know that mount was **that** weird.

---

### Post by Fittersman on 2005-12-08
none that i tried allowd me to write to the hda2 i used fmask=0000,0111,0555,0777 and dmask=0000,0111  i found that dmask=0000 probably means that i can execute the files and fmask=0000,0111 mean read (dont remember what 0555 did) fmask=0777 is bad no read

im screwed unless you guys can help me tonight it would be best if you could tell me what the fmask dmask and the numbers mean so i coulld fool around myself or anyway to get files from ubuntu to windows other than floppy because they are too large

---

### Post by Bachstelze on 2005-12-08
I told you EXACTLY what you have to put in another post, you told you were going to try it. Did it work ? (For me it did...)

---

### Post by Fittersman on 2005-12-08
o did i? i dont remember that. i will look for what you said then...

---

### Post by Grey on 2005-12-08
Ummm.... copy/paste?

---

### Post by Fittersman on 2005-12-08
i cant find what you told me to do

---

### Post by Bachstelze on 2005-12-08
so, I'll tell you again, run

```
sudo gedit /etc/fstab
```

Find the line of the FAT32 partition yu want to mount and replace whatever you put at the "options" column with this :

```
rw,user,auto,gid=100,uid=1000,umask=002,iocharset=utf8,codepage=850
```

Save the file and run

```
sudo mount -a
```

---

### Post by Fittersman on 2005-12-08
my partition is a ntfs one though so does that work also?

(i swear you follow me :D)

---

### Post by Bachstelze on 2005-12-08
No it will not. You cannot write on NTFS partitons on Linux. Well, in fact you can but the risks of losing the entire partition are quite high so it's unadvisable to do so.

---

### Post by Grey on 2005-12-08
[QUOTE=Fittersman]i cant find what you told me to do[/QUOTE]

1) Open up the txt file (double click the icon)
2) Click and drag over the text that you want to select
3) Press Ctrl-C on your keyboard (this copies to the clipboard)
4) Go back here to the forums and press Ctrl-V where you normally type stuff (this pastes from the clipboard).
5) You're done.

The reason that you have so many replies telling you to do this is because to most computer users, it's REALLY basic knowledge...  I was about to suggest going back to Windows myself, as the previous poster did.  But then I thought about it.

1)  You are intelligent and capable enough to install Linux in the first place.
2)  Linux is actually probably easier to maintain than windows once it's set up properly.
3)  You ARE asking the right people.  It should be within us to help you rather than direct you to the competition.
4)  I apologize.

---

### Post by Bachstelze on 2005-12-08
@Grey > I think this question was directed to me... Ans if I remember well he cannot go to the web with Linux (crappy winmodem...) and he wants to move files from Ubuntu to NTFS...

---

### Post by Fittersman on 2005-12-08
all i can say is that im not that dumb...

and that im goin from ubuntu back to windows to use the internet to tell you this stuff (so copy/paste not work after restart) becuase ubuntu dont have internet yet o ya and hymntolife i pasted that file you wanted somewhere. :D

---

### Post by Grey on 2005-12-08
[QUOTE=HymnToLife]@Grey > I think this question was directed to me... Ans if I remember well he cannot go to the web with Linux (crappy winmodem...) and he wants to move files from Ubuntu to NTFS...[/QUOTE]

I see.  Well then.  I'll let you take over because you seem to know what's going on with him.

---

