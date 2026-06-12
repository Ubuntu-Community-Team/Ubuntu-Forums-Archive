---
title: "Magick Rotation"
date: 2012-04-27
forum: Hardware
---

### Post by dog-soldier on 2012-04-27
on my Fujitsu t4210 tablet pc i tried for 3 hours last nite to get Magick Rotation to work. i got frustrated and went to bed. this morning i tried for a couple more hours but no go.
i thought i would try to use the script i used when i ran 11.04 which works except for when i rotate the screen the stylus is messed up. if i use the mouse all is good. 
im not sure what im doing wrong when i tried to get Magick Rotation to work but it drove me nuts and gave me a headache since i would love to get the rotation working right.

---

### Post by Favux on 2012-04-27
Hi dog-soldier,

What version of Magick Rotation did you use?  Revision 45 on the devel branch?

Did you install the fujitsu-tablet dkms?  Did that go without problems?

---

### Post by dog-soldier on 2012-04-27
that was one of the problems i was having was trying to install the  fujitsu-tablet dkms. i just couldnt figure out how to install it.

it was Revision 45 that i tried.

---

### Post by Favux on 2012-04-27
Alright, were you able to install Magick Rotation itself OK?

For the dkms you may not have been in the correct directory.  Assuming you downloaded and extracted on the Desktop it would be something like:
```
~/~magick-admin-team/magick-rotation/devel
```
And in the devel directory folder is the MagickExtras folder.  Is that what you have?  If so right click on the devel folder and chose Copy and Paste it on your Desktop.  Then right click on the copied devel folder on the Desktop and rename it 'magick-rotation' (without the quotes).  That will get you to where you'd be with the release tarball and simplify the directories for you.

---

### Post by dog-soldier on 2012-04-27
> **Favux said:**
> Alright, were you able to install Magick Rotation itself OK?

For the dkms you may not have been in the correct directory.  Assuming you downloaded and extracted on the Desktop it would be something like:
```
~/~magick-admin-team/magick-rotation/devel
```
And in the devel directory folder is the MagickExtras folder.  Is that what you have?  If so right click on the devel folder and chose Copy and Paste it on your Desktop.  Then right click on the copied devel folder on the Desktop and rename it 'magick-rotation' (without the quotes).  That will get you to where you'd be with the release tarball and simplify the directories for you.

i was able it install magick rotation, i just clicked ans ran. i found the dkms last nite and i ran into the same problem just now . i followed the instructions found in the fujitsu-tablet_README.txt . 
```
dogsoldier@dogs:~$ sudo cp -a /home/dogsoldier/Desktop/magick-rotation/MagickExtras/fujitsu-tablet-20120404-gerlach /usr/src/
[sudo] password for dogsoldier: 
dogsoldier@dogs:~$ sudo dkms add -m fujitsu-tablet -v 20120404-gerlach
sudo: dkms: command not found
dogsoldier@dogs:~$ 

```

and this is as far as i can get. not sure where i went wrong.

---

### Post by Favux on 2012-04-27
Good, so we just need to get the dkms implementation of fujitsu-tablet set up.

Can you use Nautilus to navigate to /usr/src and see if the folder fujitsu-tablet-20120404-gerlach is in it?

What version of Precise did you install?

---

### Post by dog-soldier on 2012-04-27
> **Favux said:**
> Good, so we just need to get the dkms implementation of fujitsu-tablet set up.

Can you use Nautilus to navigate to /usr/src and see if the folder fujitsu-tablet-20120404-gerlach is in it?

What version of Precise did you install?

yes fujitsu-tablet-20120404-gerlach is in usr/src.
im using unity if thats what you mean.

i installed the beta and ran updates

---

### Post by Favux on 2012-04-27
OK.

Then the next question is do you have the dkms framework installed?  In the Software Center search 'dkms' or at the command line:
```
sudo apt-get install dkms
```

---

### Post by dog-soldier on 2012-04-27
ok thats where i went wrong, didnt install dkms framework.
after i did that i was able to go thru rest of the list and sit it up. after i rebooted i rotated the screen and it worked along with the stylus. 
works like a charm.
do i need to keep the magick rotation folders on my desktop or can i get rid of them?

once again you helped me with the screen rotation and i give you a huge kudos for it.:popcorn:

---

### Post by Favux on 2012-04-27
Outstanding!  :)  Thank you.

You're the first Fujitsu tablet PC user to report success!!!  I had begun to despair.

No you do not need to keep the folders.  But there is an uninstaller in the MagickUninstall folder and your install log and the READMEs.  You may want to keep them.  Move them to somewhere in /home/yourusername maybe.

Alright.  So it appears I need to mention installing the dkms framework in the dkms README's.  Not everyone will have installed a proprietary video driver or whatever and have the dkms framework already installed by doing that.  Thanks for pointing that out.

---

### Post by Favux on 2012-04-29
**[SIZE="3"]FYI Update:[/SIZE]**

I've updated the README with instructions to install the DKMS framework and pushed Fujitsu tablet PC support to Magick's unstable branch.  So there is a new tar to download.  The new instructions for Fujitsu tablet PC users is on the "[Magick Rotation for Fujitsu tablet PC's]("http://ubuntuforums.org/showthread.php?t=1967982")" thread.

---

