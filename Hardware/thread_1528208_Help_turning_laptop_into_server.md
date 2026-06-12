---
title: "Help turning laptop into server"
date: 2010-07-10
forum: Hardware
---

### Post by MyBIOS on 2010-07-10
Now I know it's not the best of options for a home server but I have one laying around and it will do for our media needs.  I have been attempting to install Ubuntu Server and ended being told by my roommate that I could just configure the desktop version to suit our needs.  Is there any walkthrough for this or any tips you can offer?  It's my first time doing this and I am having a fun (although stressful) time trying to set everything up and running, not to mention learning more in one night and morning than I thought I could.  Thanks for any help you can give!

---

### Post by mörgæs on 2010-07-10
Hi, welcome to the forum (and to Ubuntu).

If you mean a file server, best is to set up Samba. There are plenty of tutorials on the web; one of them is 
[http://www.jonathanmoeller.com/screed/?p=1590](http://www.jonathanmoeller.com/screed/?p=1590)

There are also lots of useful posts on this forum.


Samba will allow Linux and Windows clients to access files stored on a Linux machine.

---

### Post by MyBIOS on 2010-07-13
I guess I should also explain what I want my server to do.  I want to connect to it at home (along with my roommates computers) and allow us to read, write and delete with our own separate computers (I am not sure which configuration would be best), access it from another computer outside our network (like if I want to download a file I have on my server to my friends computer at their place) and I'd like my laptop to forward a downloaded torrent file to my server and for my server to download it using a bit torrent client (I am not sure if I need Transmission or BitTornado).  

I have thought about doing this:

[http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1)

I am not sure if his configurations allow for anyone to connect to it under one name, just as long as they have the password or how secure it is.  

I have also been reading:

[http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)
 
and 

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

and again I have the same concerns.  I am just confused by all the discrepancies in the configuration files for Samba and proFTP and don't know what to do!  If you think I should just follow either tutorial or if you have any helpful suggestions for my situation it is much appreciated!

---

### Post by mörgæs on 2010-07-13
You have a lot of plans. My only suggestion is to do the project in small steps.

Begin with Samba, for example:
[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Samba_File_Sharing](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Samba_File_Sharing)

That will enable file sharing on the inside of the firewall. When that is done, you can focus on getting through the firewall.

---

### Post by MyBIOS on 2010-07-13
Great thanks, I am going to scour that later today once I know what I need to install.  I still am not quite sure what I'll need to get the results I want.  I know I need to set up the samba server for connecting while at home and for the roomies, if I want to grab something from it at a friends house do I need to install proFTP or will openSSH take care of that?  And as for the torrent forwarding would squid take care of that?  Or would installing a VNC be the best way to grab stuff and transfer things?

---

### Post by MyBIOS on 2010-07-13
as you can see I am not used to networking and it is quite intimidating.  I am just clueless and anxious

---

### Post by IcarusR on 2010-07-13
I agree you are best off doing as mörgæs suggested & take it in small steps. 
Start by getting samba setup & working over local network first.
The webpage mörgæs linked should get samba working for you.
Any specific problems post here & someone will try to help.

---

### Post by MyBIOS on 2010-07-13
okay, thanks a lot for the pointers.  I have got samba up and running and I can access the files that are in /home/media.  I also have an external that I plugged in and created a symlink to access it from the CLI in my server.  When I tried to access the external through the symlink from my mac, it showed up as a broken alias.  what do I do in this case?

---

### Post by MyBIOS on 2010-07-13
Well I tried to change a share in the .conf to get the external to connect and that didn't work, so then I changed it back and that still didn't work.  I reset smbd and nmbd and it still didn't work so I rebooted.  I had configured it to login automatically on startup and then it brought me to the start up page and wouldn't accept my password.  It looked like it would, then it would bring me to a cli screen and then back to the sign in window and played the invalid input sound.  I tried the only other password that it might be and it still wouldn't accept it.

---

### Post by mörgæs on 2010-07-14
If I get this right: Are you saying that the problem is a lost password? I don't think that I can help with that.

---

### Post by MyBIOS on 2010-07-14
W

---

### Post by MyBIOS on 2010-07-14
> **mörgæs said:**
> If I get this right: Are you saying that the problem is a lost password? I don't think that I can help with that.

What?  No.  Quit being so haughty and give me more credit than that.  It rejects incorrect passwords and says "Authentication Failure".  For the correct password it looks like its going to login, then goes blank for a second and then brings me back to the login page.  So something is wrong and I have no idea of what it is.  I am going to do a fresh install again and set up the samba server again. 

 I also have an external hdd that I want to mount to the computer so we can use that too.  Once I have samba up and running again should I create a permanent mount in the share directory?  Or will I have to do something else?

---

### Post by MyBIOS on 2010-07-14
bump

---

### Post by IcarusR on 2010-07-14
> should I create a permanent mount in the share directory

You can do that, or if you want the external drive to show up as a separate drive in Nautilus then create a separate share in your smb.conf & separate mount point outside all other shares. 
Also if it is a separate share then should you wish to restrict who uses it it will be much easier.

---

### Post by IcarusR on 2010-07-14
When you get it up & running again you can use NoMachine NX to pull an X sesion complete with Gnome over to your desktop.

[http://www.nomachine.com/]("http://www.nomachine.com/")

Howto here...

[http://ubuntuforums.org/showthread.php?t=941530]("http://ubuntuforums.org/showthread.php?t=941530")

NoMachine NX is much smoother than any VNC setup I've used & does not have the lag either.

Or for plain administration Webmin (in the repos) is good...

[http://www.webmin.com/]("http://www.webmin.com/")

---

### Post by MyBIOS on 2010-07-16
So I had one share set up on the internal hdd and I was able to write and take from a few of the directories that I created and so I made a share on smb.conf for my external.  I got rid of the initial share code ( I just want to write directly onto the external instead of internal ) and replaced it with the following (swag is the name of my external ):

[swag]
path = /media/swag
read only = no
browseable = yes
writeable = yes

I restarted smbd and nmbd and went back to my macbook to see if I could access the external, but then I couldn't access the server at all, I did cmd+k and chose my server but it said I didn't have access to it and it kept trying to connect and bringing up the access denied message, like an infinite loop.  I had to keep rapidly hitting enter and try and hit the little x-button on the connect window with my trackpad to cancel the connection attempt.

So I rebooted the server and powered down the external and when I went to log back in the same thing happened!  When I hit enter the screen went to a blank CLI with flashing cursor, then made the start up bongo noise and brought me to the login screen.  I tried typing an incorrect password and it said "Authentication Failure" so it was obviously accepting the password but something is wrooong!  My only guess is that I uninstalled something when I was trying to slim down the OS ( Ubuntu Desktop 10.04 ) with Synaptic that I shouldn't have.

So I guess my questions are:

1) Was I on the right track before I couldn't log in?
2) How do I fix this login bug?!?!?

Thanks for your all your help with this too, I am learning a lot and really enjoying the process of making my own server!

---

### Post by IcarusR on 2010-07-16
If you are going to remove packages from your install I would suggest you do that first & test it, including rebooting. 
Then once you are happy it works OK then install & set up Samba.
One step at a time, it makes trouble shooting much easier.

Another tip, I image all my boxes once I have them setup & customised. 
Then if they go bad it is quicker to re-image than reinstall & setup again.

---

### Post by MyBIOS on 2010-07-16
Oh man great thinking :D

---

### Post by MyBIOS on 2010-07-17
Alright!  I have a server up and running with a system that reboots properly and mounts everything fine! \\:D/ 

The only problem right now is that I have my share set to my external that I have connected to the server, but I can only read from it, I cannot write to it for some reason.  Here's my share:

[swag]
path = /media/swag
valid users = media
writable = yes
browsable = yes
create mask = 0700
directory mask = 0700

My best guess is it's something wrong with the parameters in smb.conf but that's a shot in the dark

---

### Post by IcarusR on 2010-07-17
Are you trying to access as user 'media' as in smb.conf ?? 
'valid users' are the only users that can 'use' share & must have read/write access to the mount point. ie either own it or it must be set to 0777

Personally I have all my shares mounted to their own mount point created in / with permissions set accordingly on them. 

To test smb.conf from server run..

```
testparm
```

---

### Post by MyBIOS on 2010-07-18
Yup, my username is 'media' also.  Would that cause problems?  My external is also hfsplus formatted, I don't know if that makes a difference.  How can I change the mount point of my external?

---

### Post by MyBIOS on 2010-07-18
Turns out my external needed some minor repairs, so I'm in the process of that.  Maybe that was why...

---

### Post by MyBIOS on 2010-07-19
Well, I repaired the disk and changed the path in the [test] share to ' / ' and was not able to  write to the internal hdd either.  I've created an smbd username with:
asudo smbpasswd -a media

and still can't write to it.  Any ideas?

Again, thanks for all your help IcarusR, much appreciated!

---

### Post by MyBIOS on 2010-07-19
Hmmm, I found the directory that I can write to in /home/media, my user name haha :)  Wow.  Well that helps a lot.  So will I have to change the mount point of 'swag' to /home/media?  Time for Google!

---

### Post by IcarusR on 2010-07-19
My shares are mounted to 

```
/music
```

This directory is owned by my username & set to 777 (yes I know security issue) ls -l 

> 
drwxrwxrwx 470 andy andy 20480 2010-07-16 20:28 music

It is mounted at boot with a line in /etc/fstab


> /dev/sda1                                  /music          ext3    defaults                   0       2

On remote box share is mounted to ~/andy/music with the following /etc/fstab line

```
//Florence/music          /home/andy/music   cifs   netdev,credentials=smbcredentials,  0 0
```

The credentials=smbcredentials is to allow auto mounting with out the need for me to enter password every time.

---

### Post by MyBIOS on 2010-07-19
My external is a WD My Book 1TB that I formatted with my Mac when I first got it ( so it's hfsplus ).  Even when I try to access it from the Ubuntu desktop it says that it is read only.  Does the external have some configurations that I need to change?  It works fine from my Macbook but not with anything else!

---

### Post by MyBIOS on 2010-07-19
I have read that I need to turn journaling off, but will that allow Ubuntu to write to hfs+?  And if so, how do I turn journaling off?

---

### Post by IcarusR on 2010-07-19
This page tells how to turn journaling of from your mac

[http://castyour.net/node/40]("http://castyour.net/node/40")

This thread says that installing hfsprogs then running fsck fixes it.

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=239370]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=239370")

```
sudo fsck.hfsplus /dev/sdX
```
where sdX is what ever number your hfs partition shows up as.

---

### Post by MyBIOS on 2010-07-21
Finally!  I finally have it up and running!  Thanks a million for all of your help IcarusR!  You're a gem!  Thank you!  My next task is to set up NoMachine!  Hopefully that goes smoother than this haha.  I'll start a new post for that though so maybe this time it won't be only you helping me!  Thanks again

---

### Post by MyBIOS on 2010-07-21
derp.  Actually, I think that more of what I was thinking of was being able to download the files from my server to a friends computer, is an FTP server what I need?  I guess preferably I'd like to use a web browser ( but I am worried that would be muuuuuuch to complicated ) but was thinking that Filezilla would work too.  Any different suggestions?

---

### Post by IcarusR on 2010-07-21
Do some reading first. Search the forums, there are some good guides, & google.

If your mate is on the same network he can be setup to have access to your samba share.

NoMachine (easy to setup, is a guide somewhere on forum) is for remote access to administer server not transfer files.

---

