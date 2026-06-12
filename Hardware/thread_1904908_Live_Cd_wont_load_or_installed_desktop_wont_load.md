---
title: "Live Cd wont load or installed desktop wont load"
date: 2012-01-05
forum: Hardware
---

### Post by cep3431 on 2012-01-05
I have a Dell Inspiron 2500, It had Windows ME on it and ran fine. I Upgraded the ram from 64mb to 192mb it ran faster but i wanted linux so i tried to boot the xubuntu live cd it went to a black screen and didnt change even when i left it for a few hours. I installed xubuntu via alternate install cd and install went fine, when i booted it it it went to a black screen and an "X"  (like a cursor)showed up for a second. I can get to the terminal by pressing ALT+F2 and get to a login.  I dont have high speed internet at home so im going to try to install lubuntu when i get home. I think it might be a graphics issue but i dont know where to start.
[B][SIZE=2]
[/SIZE][/B]

---

### Post by Paddy Landau on 2012-01-06
I think Lubuntu would be a better bet. Xubuntu ideally wants at least 256Kb to install (unless you use the alternative installer), but even once installed, 192Mb RAM is too little for a good system. Xubuntu recommends at least 256Mb, but prefers 512Mb or more.

Lubuntu is happy with 192Mb, although it would prefer more.

---

### Post by cep3431 on 2012-01-07
Today I tried to install lubuntu but the same thing happened. I want to install mythbuntu I know i will have to upgrade the ram but i want to make sure I can get a *buntu to install.

---

### Post by Paddy Landau on 2012-01-07
If this happens with Lubuntu, then there is something wrong and increasing your RAM is unlikely to solve it.

Unfortunately, I do not know how to solve this, so I think you need to start a new thread on the [Installation & Upgrades]("http://ubuntuforums.org/forumdisplay.php?f=333") thread, indicating that you have tried this with both Lubuntu and Xubuntu.

---

### Post by upchucky on 2012-01-07
you have a display issue that needs to be investigated, you may also want to look at puppy linux or other small installed footprint versions for such a small machine.
I suspect that the display issue will be a challenge in whatever flavor of Linux you try. The display can be challenging to set up but a good place to start is with X11 or Xorg depending on which version of Linux you choose.
You will have to manually edit those files to suit your dispaly type.
Again you will have to do lots of googling and reading to figure out how to get the display working properly.

---

### Post by cove19 on 2012-01-07
Can you tell us which version of XUbuntu you were installing. I have been having trouble with LinuxMint 11 and 12 on a Acer Travelmate and the issues were the same as the original post from cep3431.

The flavour of Mint was LXDE for 11 and Gnome for 12. I couldn't however get to terminal with alt + f2. I had to simultaneously press del + break + ctrl + alt to get a dialogue to log out. There I was able to change the flavour (environment) to gnome classic which worked, sort of for some reason. I then managed to get terminal up and put XFCE on as my flavour. XFCE caused me no issues. I however prefer LXDE. I have how gone down the route of installing LUbuntu 11.10 over the top of the Mint XFCE 11 and wiped Mint off along with Gnome.

[http://superuser.com/questions/28781/how-to-remove-the-ubuntu-gnome-desktop-after-making-the-switch-to-kde](http://superuser.com/questions/28781/how-to-remove-the-ubuntu-gnome-desktop-after-making-the-switch-to-kde)

I used the below prior to the command lines in the above thread.

LUbuntu 11.10 (32 and 64 Bit)
For a full install use

sudo apt-get install python-software-properties
sudo apt-get install lubuntu-desktop
sudo apt-get dist-upgrade
sudo apt-get autoclean
sudo rm /var/cache/apt/archives/*.deb

For just the core use

sudo apt-get install python-software-properties
sudo apt-get install lubuntu-core
sudo apt-get dist-upgrade
sudo apt-get autoclean
sudo rm /var/cache/apt/archives/*.deb

Even though my Acer Travelmate has 2ghz Intel 4 and 1gb RAM it wasn't happy LinuxMint not the it's LXDE or Gnome flavour yet LUbuntu 11.10 and Ubuntu 11.04 work fine. Little gremlins in the works I think for me.

What I've put above may of be no help to you, but I thought I'd share my experience as they sounded similar.

Cheers



------------------------------------------------------------------

Microsoft will never see another HDD of mine. Virus ridden operating systems from the start.

---

### Post by cep3431 on 2012-01-07
I used xubuntu 8.04 & lubuntu 11.04. I also tried DSL and it worked fine.

---

### Post by cove19 on 2012-01-08
> **cep3431 said:**
> I used xubuntu 8.04 & lubuntu 11.04. I also tried DSL and it worked fine.



I read in February's Linux Format magazine that there is are a few bugs in the LinuxMint 12.
You had issues with XUbunt 8.04. Hmmmmm. Try 9.10. that seems a very stable version from what I have read.

DSL, Puppy Linux and Slax 6.1.2 are small  live CD distros so you won't have issues there.

I have managed over night to convert LUbuntu to Ubuntu but not running in Unity for some reason. Managed to get my other PC with Intel celeron 2.8ghz and 2gb RAM working with all distros I have tried. Just the Acer Travelmate laptop stroggled. Maybe the quoted system requirements that I have read have been wrong and these distros run better with high end kit.

What are you running now?

---

### Post by LinuxFan999 on 2012-01-08
Debian 6.0.3 + LXDE is another good choice because it is lighter weight and more stable than Lubuntu.

---

