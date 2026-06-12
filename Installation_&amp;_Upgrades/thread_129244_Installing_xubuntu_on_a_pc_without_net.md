---
title: "Installing xubuntu on a pc without net"
date: 2006-02-13
forum: Installation &amp; Upgrades
---

### Post by Ghetto_Smurf on 2006-02-13
Hey all,

so, i got this p3 733mhz with 128mb (will have 512mb in the future), and ubuntu is so damn slow. I've read a lot about xubuntu, and i want to give it a try. Problem is: No internet. And i am too lousy to steal an ethernet cable com the pc's back in school to link this p3 to my uncle's celeron to use the default instalation of xubuntu.

So, were can i get (or create) a .deb file of xubuntu? Or should i wait to get the 512mb and use ubuntu lite? And waht about fluxbox? I got the .deb from debian file repository.

---

### Post by earobinson on 2006-02-13
in your sources.list just type the address in your web browser and that will let you look at the repos and dl the debs you need. It will be a lot of debs, if you do do this and want to make an iso post a torrent link on the site im sure lots of people would like this.

**WE SHOULD CHECK WITH THE ADMINS BEFORE WE POST ANY TORENTS TO THE SIGHT EVEN IF THEY ARE LEGAL IM NOT SURE OF THE FORUM RULES ON THIS**

EDIT 01: I Have msged the admins about this
EDIT 02: ubnuntu-geek said he has no problem if you want to make the iso.

---

### Post by Ghetto_Smurf on 2006-02-13
doesn't anyone have a log of the .deb files that ubuntu downloads when you use [FONT="Garamond"]sudo apt-get install xubuntu-desktop[/FONT] ?

it would really help me :mrgreen:

---

### Post by earobinson on 2006-02-13
what you could do is man apt-get, and find out how to use the download only option. Then on a computer with the internet download all the needed files. Should have thought of that in my first post, I would look up the command but im not on my ubuntu box :(

Also the admins seem to have no problem with you posting a torrent after you are done (as long as it is only legal deb files of cource)

---

### Post by Adrian_b on 2006-02-13
[QUOTE=earobinson]what you could do is man apt-get, and find out how to use the download only option. Then on a computer with the internet download all the needed files. Should have thought of that in my first post, I would look up the command but im not on my ubuntu box :(

Also the admins seem to have no problem with you posting a torrent after you are done (as long as it is only legal deb files of cource)[/QUOTE]

Are all the .deb's deleted on install?
And if you do the download only option, where will the .deb be?

---

### Post by Ghetto_Smurf on 2006-02-13
2 questions:

how can i search for the .deb files when i don't have internet on the computer? maybe i can use the LiveCD on this pc and do the commands, but i had lots of problems using knoppix, because the graphics card on this pc in onboard, and it sucks. the only thing it works was suse an slax, and both of them didnt had the title bar on kde:( . If anyone out there using xubuntu had the logs it would be helpful

2º,
can i use gdesklets on xfce?

---

### Post by earobinson on 2006-02-14
I was assuming you had a ubuntu computer on the net and a ubunut computer off the net, is this not the case?

gdesklets will work with xfce

as for where the debs are saved man apt-get for that info

---

### Post by Ghetto_Smurf on 2006-02-14
apt-get does remove the deb files after they are installed.

i have an windows box with net, and a ubuntu box without internet. 

well i have been seachrng and i found on debian's file repository the xfce .deb files. but there are a lot of dependencies. i will try to put them all in a .tar so i can put them in ubuntu. or maybe ill just steal that ethernet cable forum school and make a connnection so i can have net on ubuntu. don't need it, i just do my tipping work and listen to music, but i'll connect it to the internet just to get xfce working.

---

### Post by BenTyreman on 2006-02-14
apt does not remove the .deb files. They are stored in /var/cache/apt/archives/ until apt-get clean is run.

To install xubuntu on a machine without an internet connection, apt-zip sounds like the way to go. Apparently, when run on the PC you want the package installing on, it generates a script that can be transferred to a machine with the internet. The script downloads and packages the relevant files. You then transfer this back to the target PC, and run apt-zip again.

---

