---
title: "Lost but not found. Google Earth Launcher"
date: 2008-11-05
forum: General Help
---

### Post by Velvetelle on 2008-11-05
I know this has probably been posted up here somewhere before, but i am having real trouble finding the launcher for Google Earth for Linux that i installed today. 
I have read through a few of the google search results and they all come up with the same thing /usr/local/google-earth/ and  /usr/local/bin. but they simply do not work, i get No such file or directory (one of those) and this is driving me nuts to be honest.

Can someone***_[COLOR="Red"] PLEASE[/COLOR]_*** help me out...

Yes i am a recent convert from Windoze but hey, no one is perfect in the beginning right?

I gotta start somewhere...

---

### Post by quibbler on 2008-11-05
Try /usr/bin/googleearth

Regards quibbler

---

### Post by oldos2er on 2008-11-05
> **Velvetelle said:**
> I know this has probably been posted up here somewhere before, but i am having real trouble finding the launcher for Google Earth for Linux that i installed today. 
I have read through a few of the google search results and they all come up with the same thing /usr/local/google-earth/ and  /usr/local/bin. but they simply do not work, i get No such file or directory (one of those) and this is driving me nuts to be honest.


 Run these two commands in the terminal:

sudo updatedb

whereis googleearth

 The first command may take a minute or two to complete. How did you install Googleearth? From the repositories, or the *.bin?

---

### Post by Velvetelle on 2008-11-06
> **oldos2er said:**
> Run these two commands in the terminal:

sudo updatedb

whereis googleearth

 The first command may take a minute or two to complete. **How did you install Googleearth? From the repositories, or the *.bin?**
I tried that command in the terminal and the result i got was this...

[I]user@user-desktop:~$ sudo updatedb
[sudo] password for user: 
whereis googleearth
user@usera-desktop:~$ whereis googleearth
googleearth:
user@user-desktop:~$ [/I]

(this means nothing to me)


I installed it from the Bin file.

I found the instructions on the GE website, i guess that was not the best way to do it huh?

How do i add a program to the repositories?

Like i said i am new at this but very eager to learn let me tell you...

Thanks guys for your replies, its really appreciated.

---

### Post by nothingspecial on 2008-11-06
Istallation instructions for google earth are here

[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

You may want to use the instructions halfway down the page to remove what you have installed then install it from the medibuntu repository. To do this copy and paste these commands.


```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list

```
```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install googleearth
```

Alternatively you could just type ```
googleearth
```
to run what you already have.

Or try looking under applications > internet and see if the launcher is there.

---

### Post by Velvetelle on 2008-11-06
Nothing special, you are something special.

A GREAT big thank you, it actually worked and its brilliant...

Can i ask you if i need anymore help????? :biggrin:

---

### Post by sdowney717 on 2008-11-06
I downloaded the installer directly from google.
It shows as a menu item in applications-internet-google earth

After making it executable, I Installed it like this

sudo ./googleearthfilename.bin

scott@scott-desktop:~$ whereis googleearth
googleearth: /usr/lib/googleearth /usr/local/bin/googleearth
scott@scott-desktop:~$

---

### Post by nothingspecial on 2008-11-06
Any time. 

I was as lost as anyone when I started this, I just try to pass on what I`ve learned.

---

### Post by oldos2er on 2008-11-06
> **Velvetelle said:**
> I tried that command in the terminal and the result i got was this...

[I]user@user-desktop:~$ sudo updatedb
[sudo] password for user: 
whereis googleearth
user@usera-desktop:~$ whereis googleearth
googleearth:
user@user-desktop:~$ [/I]

(this means nothing to me)


I installed it from the Bin file.
  

 That output means nothing was found. Are you sure it's installed? Normally the commands you'd run to install the *.bin would be:

chmod a+x GoogleEarthLinux.bin

sudo ./GoogleEarthLinux.bin

---

### Post by Velvetelle on 2008-11-07
Hey yep thanks i did what nothing special said to do and it worked brilliantly... And the icon in in the Apps>Internet>Google earth  so yeah and it works great now

Thanks for the help everyone...:)

---

