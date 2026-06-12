---
title: "Debian GNU/Linux question"
date: 2008-07-19
forum: General Help
---

### Post by Twitch6000 on 2008-07-19
Ok I am trying Debian GNU/Linux Lenny and have it installed.

The only problem is this,I start it up and it comes to a command line type thing and ask for name and pass(like arch did).

I was like ok no big deal.

I expected after it to start the DE,WM,and all the other stuff.

It did not :(.So how do I get debian to act like other distros?

I know debian is suppose to be hard to install,but come on lol.

Anyways I know one of you can help :).

---

### Post by ubuntu27 on 2008-07-19
When I installed Debian for the first time, I also had the same problem as you. There was no GUI.

The problem was that in one of the installation process, I did not specify that I wanted a working desktop environment.

People here may be able to help you in "fixing" or adding the GUI. But, if you are desperate, RE-ISNTALL DEBIAN AGAIN.

PAY ATTENTION to the install's question. There is a part where it says what would you like to install. a) Desktop b) Laptop C) Minimal [Something along those lines]

The thing was that I have choosen "minimal install", I though that minimal included GUI ><; but I was wrong.


**Choose Desktop** and you should get a working graphical environment.



NOTE: You can have a Graphical Install by

When you boot to the Debian's CD you can see the first screen with [U]boot: prompt[/B] type &#8220;**installgui**&#8221; (without quote marks) and then press enter. :)

---

### Post by Marinski on 2008-07-20
If you use installgui the only thing you will have is GUI during the install itself, it doesnt guarantee you a running desktop environment. My suspicion is similar to ubuntu27's - are you sure you have actually installed any desktop environment (KDE/Gnome/something) and desktop manager? If you select to install Graphical environment while installing Debian the default installed is Gnome. If you want KDE you have to choose only base system and install kde later. So I suggest that you login, gain root privilegies and type:
for kde:
apt-get install xorg kde kdm

and for gnome(not really sure on that - I'm a KDE user):
apt-get install xorg gnome gdm

Then after a reboot you should have all the bells and whistles :)
Cheers!

---

### Post by rossjman1 on 2008-07-20
sudo apt-get install gnome/kde
sudo apt-get install gdm/kdm/xdm
gdm/kdm/xdm

---

### Post by koenn on 2008-07-20
you can probably also just run **tasksel** at the command prompt
it gives you a list of options, where you can select "Desktop System" (or something like that).

---

### Post by Twitch6000 on 2008-07-20
Pheew thank you people I will try this.If anything I will reinstall lol.
Maybe this is why arch didn't like me <.<.

Anyways I will try this out and be back with the update thanks for the help.

---

### Post by Twitch6000 on 2008-07-20
Ok update

I tried doing what you all told me.The out come came to nothing :(.
I think I may have an old version or something due to it not getting internet.
Plus it not having some options you all have mentioned.
So could someone point me in the direction of the latest unstable or testing version of debian :)?

---

### Post by Twitch6000 on 2008-07-21
*bump*

---

### Post by perlluver on 2008-07-21
[http://www.debian.org](http://www.debian.org) download the net install CD, and make sure you select desktop when installing it.

---

### Post by Twitch6000 on 2008-07-23
Ok I have lenny installed now a new mean problem.
Debian looks great and such,but it doesn't see my wireless and does not come with anything.
Only things it came with were two web browesers,terminal,package manager(i was happy about that until no wireless help lol),and the basic stuff.

Can someone post a .deb file to install the intel wireless 3945abg card.

I really wanna give debian a try,but it hates me so much.I may go back to PClinuxOS or distrohop to another loving distro :/.

---

### Post by Twitch6000 on 2008-07-24
Someone can close this now

I have just went back to Ubuntu and PClinuxOS08.

---

