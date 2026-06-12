---
title: "Total Linux / Ubuntu Virgin! HDD help"
date: 2006-02-09
forum: Hardware &amp; Laptops
---

### Post by Blind-Summit on 2006-02-09
Hi everyone. Just firstly want to say how pleasant the community feels as a newcommer. I can't stress how nice it was getting my free Ubuntu 5.10 cds in the post - all free!

Right, I have lived with Windows since 3.1 and have been running XP on this PC for a few years. I have always wanted to try linux but have failed. I have tried debian (couldn't install on SATA) and managed to run Knoppix on the Live CD. I wanted to install a hard copy, and was directed towards Ubuntu. 

With a little shuffle about of some files, i made a new 10GB NTFS partition under windows to run Ubuntu. I installed and had to delete the 10GB partition and let it create the swap file and second partition for the main install. This all went fine but can no longer see the 2 new partitions under windows (this is expected I presume)

Anyway - here are the questions in order of importance:

1. Network Support. I have a belkin 125mbps wireless PCI card (think it;s 7100uk version) and this is not detected under Ubuntu. I only see my two onboard LAN ports. How can I install the drivers to allow me to connect to my wireless router / the internet.


2. Sound. I have an ASUS A7N8X motherboard with onboard sound. I use a SPDIF output to take a digital signal to my home cinema amp. I think I can detect the sound as nforce2 (my chipset) but can't play any of the sounds (I tried to play the wav files listed on the sounds config window)


3. Detecting SATA NTFS drive. I have files and music etc on my second harddrive that i would like to access. As it stands, I have this setup:

80GB SATA - 2 Windows partitions - NTFS (windows + programs/documents)
                - 2 Ubuntu partitions - don't know the FS but can't see them in windows
160GB SATA - no partitions - NTFS (storage drive, music / video etc)

I would like to get the music and video from the second drive, and my documents and images from the first drive. The drives are sda and sdb. I have read that mount -t ntfs -o errors=recover /dev/hda1 /mnt/win_c would work. I guess I would use sdb1 instead og hda1 and the win_c is just a label?


4. Video Support. (I decided to list this all here instead of the video / network sections to keep track of my problems) I have a GeForce Ti 4600 AGP card. I have it setup under windows with dual monitor. Is there any way to have dual monitor support in Ubuntu?


I appreciate any help, and apologise that I cann't undestand the help given to others with similar issues. I see the commands like sudo lshw -c network etc and mount -t ntfs . . but they mean very little. I understand they are commands, but wouldn't know where to enter them as i can't find the command line tool.

I apologise for the simplicity of these problems, but am looking to setup the basics and then to take some time to learn the rest myself. I also give my thanks in advance for any help.

Alex

---

### Post by el3ktro on 2006-02-09
[QUOTE=Blind-Summit]
3. Detecting SATA NTFS drive. I have files and music etc on my second harddrive that i would like to access. As it stands, I have this setup:

80GB SATA - 2 Windows partitions - NTFS (windows + programs/documents)
                - 2 Ubuntu partitions - don't know the FS but can't see them in windows
160GB SATA - no partitions - NTFS (storage drive, music / video etc)

I would like to get the music and video from the second drive, and my documents and images from the first drive. The drives are sda and sdb. I have read that mount -t ntfs -o errors=recover /dev/hda1 /mnt/win_c would work. I guess I would use sdb1 instead og hda1 and the win_c is just a label?
[/QUOTE]

First of all: Welcome to the Linux world. You'll soon see that many things are totally different here. Okay, it's absolutely normal that Windows doesn't "see" your two Linux partition because Windows doesn't work with anything except MS filesystems. Linux can READ from NTFS drives, but you won't be able to write to them. This is because MS has not made the NTFS specifications available to the public, so nobody excet MS knows how to write to NTFS partitions :-(

If you really want to dual-boot with Windows, the easiest would be to store all your data on a FAT32-partition which both Win & Linux can read&write.

The mount command you gave - mount -t ntfs -o errors=recover /dev/hda1 /mnt/win_c - is correct. With -t you tell mount which filesystem the partition has (this is not needed with most filesystems, munt can find out automatically). The "-o errors=recover" is not necessary imho on NTFS. You're correct that you have to replace /dev/hda1 with the partition you want to mount, in this case it would be your 160GB drive. The last argument "/mnt/win_c" tells Linux where you want your Windows partition to be mounted. I'd suggest something like /meda/data or so. You could also create a directory within your home folder and mount your Windows data there for easier access.

> 
I appreciate any help, and apologise that I cann't undestand the help given to others with similar issues. I see the commands like sudo lshw -c network etc and mount -t ntfs . . but they mean very little. I understand they are commands, but wouldn't know where to enter them as i can't find the command line tool.


You find the command line toold in the Applications menu, it's called "Terminal".


Tom

---

### Post by Blind-Summit on 2006-02-09
Hi Tom, thanks for the welcome.

I have far too much stuff to move from Windows to reformat to FAT32. I only really need to write to the Ubuntu partitions and read the music / video from ntfs. I found the terminal on, and the menu system is pretty simple as I organise my WinXP start menu in the same way with programs / internet / office folders etc.

I keep getting told that I need root access to perform the mount. I also checked and saw that Ubuntu doesn't use the normal root system (in fact it's disabled by default) and instead we use this "sudo" command

Could you elaborate on this and let me know if I can still read my ntfs drive?

Thanks for your help so far - any ideas for the other issues?

I managed to do some checks :-D  by myself to test my wifi card. It can be see under the hardware list (like device manager in windows) but it's not present in the network settings. I see etho and eth1 which are the wired network ports. The wireless is nowhere to be seen?! What should I do?

Alex

---

### Post by el3ktro on 2006-02-09
Hi, okay first you have to know which device your data harddrive is. When it is your second harddrive with only one partition then it should be /dev/sdb1. (sda is the first, sdb the second, sdc the third and so on, and the number is the partition number)

To mount this partition you have to do

sudo mount -t ntfs /dev/sdb1 /media/data

or example. The sudo command asks your your password. If you want this drive to be mounted during boot-up (so you don't have to do it manually) edit the file /etc/fstab and add the following line:

/dev/sdb1   /media/data   ntfs   defaults   0 0

This will mount this partition whenever your computer starts.


Tom

---

### Post by el3ktro on 2006-02-09
Oh yeah your other problems ... well I don't have a wireless network so I can't help you at all with that, sorry.

Tom

---

### Post by Blind-Summit on 2006-02-09
I tried the command you gave me, but it says that it cannot find the mount point. I presume this means that there is no folder to link the other hard drive to?

It seems that looking at the folder proerties that my user does not own them - I cannot therefor make new folders?

I also managed to do a mount to /media which I think has removed the folders linking to my cdrom and floppy drives. Whilst this didn't produce an error - I still couldn't see the contents of my hard drive.

Ignoring the wireless problem, I have onboard sound and I can't get this to work. I run a SPDIF digital output and this picks up nothing. I tried the normal speaker out, but nothing here. I will maybe try when i can run the mp3 files.

---

### Post by el3ktro on 2006-02-09
In general, you have to everything outside of your home directory with sudo, so you can just do "sudo mkdir /media/data" for example. Well I would not rely on the command I gave you toomuch because I don't know your harddrive setup. You have to know which /dev/sdXX is your data partition. 

Tom

---

### Post by Blind-Summit on 2006-02-09
i guess i just need to know a few basic commands really. I know that linux is a lot more command line than Windows point ad click. I understand the drive / partition system as you say

if my first drive has a C: and D; in windows, this whould be sda1 and sda2 in linux

the second drive has just the 1 partition and hence sdb1 

sda = sata where hda = ATA

\\:D/ 

Just need to fix sound :-k

---

### Post by el3ktro on 2006-02-09
You're absolutely correct about the drives.

Well for your sound issue, did you try to use the normal headphone output? Do you hear any sound there? Also try to put headphones/speakers into the front or rear audio connector to see if your soundcard works at all. You could also try to run "alsamixer" from the terminal. Alsamixer will show you all sound outputs, and it may be that the output you're using is just muted. You can mute/unmute them b pressing "m".

Tom

---

### Post by Blind-Summit on 2006-02-09
I managed to open the sound properties. I see an nforce 2 device which i presume is my soundcard. I tried all the connections. I have onboard 5.1 with digital SPDIF out. I tried headphones into EVERY socket!

Anayway, I still have issues with the hard drive access. I made the new folder correctly, and also mounted the sdb1 partition, but i get permission denied when i click the folder. Perhaps I need to do something under windows to make it work?

Alex

EDIT - I can get sound ok when I setup via alsamixer :D thanks.

Still no luch getting the mount for sdb1 (also tried sda1 etc) to work

I managed to install my printer as well!

---

### Post by Blind-Summit on 2006-02-10
I still get the permission denied for accessing the mounted drives. Any ideas?

Also, have the wireless card issue but i wil try and fix this with that ndiswrapper thing. I have downloaded the files apart from my driver.

---

### Post by Blind-Summit on 2006-02-10
I got hold of the two ndiswrapper files and what i thought was the right inf file.

I have the belkin F5D7001 wireless pci card. I was told that the dell driver was ok for this. I tried to install the driver but upon checking (ndiswrapper -l) it said it failed.

Someone please help! I'm too new to all this to figure it out and I can't make sense of the commands that I find with google searches

Thanks in advance

---

### Post by Blind-Summit on 2006-02-11
I managed to install the wireless card using the drivers from the belkin CD and it now detcts the card and also identifies my router's signal.

I can't get onto the internet yet though. Does the ndiswrapper alter the mac address in any way as I use that to limit access on my wifi. I don't use encryption as i live in the back of beyond and nobody has wifi here!

---

### Post by disabled_20220313 on 2006-02-11
Ndiswrapper won't alter the MAC address of the card at all.

'fraid I can't be much more help than that.

Good luck

---

### Post by Blind-Summit on 2006-02-11
I had a look, and I have a totally open wireless. Nobody can access it like I said as I live in such a remote area!

I can see the ssid, but no connection. Can anyone else help - Tom?

---

### Post by evilmrt on 2006-02-13
Hey! I finally got the f5d7001 belkin card to work with ubuntu!!!!

basically I just downloaded the new ndiswrapper 1.9 (1.8 wouldnt install for me) and compiled/installed from source. then I followed along with the directions on the ndiswrapper site...everything worked fine, and my SSID came up in the scan. I accentially had the key set to restricted, when it is open instead. Then I just configured it in the ubuntu networking panel after all that, as well, and ta-da! 

I should mention that I used the bcmwl5a.inf that was in the newest windows driver download (from belkin's site) for this card. I don't know if it makes a difference, but I used the inf in the AR folder, not the IR folder. 

\\:D/

---

### Post by Blind-Summit on 2006-02-13
Hey evilmrt

I managed to get mine working as well. I used the ndiswrapper and then the inf files from the AR folder from the belkin CD. I saw my SSID a while back, but coulkdn't connect. I setup my IP as static and it's fine now. I had to tweak it each time I load Ubuntu, but i don't know wether that's Ubuntu just setting up the wireless, or if i need to edit my etc/network/interfaces file and disable the eth0 and eth0 devices (I have dual onboard LAN)

Glad you got things sorted out.

I am now stuck with getting a few other things sorted out.

Firstly, the sound settings are dreadful. I have SPDIF output from my onboard card which is 5.1. This outputs in stereo only. I can also use my notmal speaker out connection with the same effects.

I really want 5.1 to work.

Next, I can't get Rhythmbox to load my mp3 - I have XMMS working fine with mp3, but it's nice to have it all working.

Then there is dual screen. I managed to totally feck up my system (well, not totally, but everything is a disaster when you are new to linux!) I had used someone else's config file for dual monitor support on a GeForce 4 Ti4600

I have figured a lot of stuff out myself, but it's nice to be sure.

I plan on writing up all my notes online soon to help other people.

Any help on the above would be great - sound is so important for me

---

