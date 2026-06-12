---
title: "laptop specs, need a linux os to suit HW"
date: 2008-06-12
forum: Hardware
---

### Post by Fenris_rising on 2008-06-12
hi all my PC is pure 8.04. my laptop however has been flying through different flavours of linux. this is mainly down to various failures of the tried OS and the laptop. i blame the laptop primarily i will say! so far ive tried;
Xubuntu.......slow to work with and had a tendency to forget its settings
fiesty fawn.....even slower
gutsy.......even slower
puppy....faster but reboot and turn off caused major hanging
mandriva......graphics didnt get on fullstop.
Debian latest....faster than the original OS XP but couldnt get network port to configure or get the ndiswrapper to work with a USB Wireless Adapter despite a bloody hard go at both. Also their forum was so unfriendly to the noob BIG time. they could learn alot from here.
dapper drake was great..........but no longer supported i then found out lol.
Ark linux.......didnt like my laptop.
mint........couldnt get it to install

given the specs below, and i know that wont be a definitive help, what other flavours of linux can i try? preferably on a single cd, with ndiswrapper in the repo's. i'll stretch to a single DVD if warranted.
what do i do with my laptop? surf the net, email. watch DVD's. stream music/movies from my pc to the laptop.
 
CPU  VIA C3 "Nehemiah" (1.2 GHz)   
Memory  256MB DDR SODIMM PC2100   
Chipset  VIA CLE266    
Hard Drive  40 GB NB hard drive    
CD / DVD Drive  DVD / CDRW Combination Drive   
Monitor  14.1" TFT (native resolution 1024 x 768)   
Video / Graphics Card  VIA Apollo CLE266 (integrated)   
Sound Card  VIA VT1616   
Modem  PCTel HSP MR 56K   
Network Card  VIA Rhine II VT6103    
Mouse  Touchpad   
Power Supply  Lite-On® PA-1700-02    
Battery  Sole Energy Corp EM1-410C2

---

### Post by stchman on 2008-06-12
> **Fenris_rising said:**
> hi all my PC is pure 8.04. my laptop however has been flying through different flavours of linux. this is mainly down to various failures of the tried OS and the laptop. i blame the laptop primarily i will say! so far ive tried;
Xubuntu.......slow to work with and had a tendency to forget its settings
fiesty fawn.....even slower
gutsy.......even slower
puppy....faster but reboot and turn off caused major hanging
mandriva......graphics didnt get on fullstop.
Debian latest....faster than the original OS XP but couldnt get network port to configure or get the ndiswrapper to work with a USB Wireless Adapter despite a bloody hard go at both. Also their forum was so unfriendly to the noob BIG time. they could learn alot from here.
dapper drake was great..........but no longer supported i then found out lol.
Ark linux.......didnt like my laptop.
mint........couldnt get it to install

given the specs below, and i know that wont be a definitive help, what other flavours of linux can i try? preferably on a single cd, with ndiswrapper in the repo's. i'll stretch to a single DVD if warranted.
what do i do with my laptop? surf the net, email. watch DVD's. stream music/movies from my pc to the laptop.
 
CPU  VIA C3 "Nehemiah" (1.2 GHz)   
Memory  256MB DDR SODIMM PC2100   
Chipset  VIA CLE266    
Hard Drive  40 GB NB hard drive    
CD / DVD Drive  DVD / CDRW Combination Drive   
Monitor  14.1" TFT (native resolution 1024 x 768)   
Video / Graphics Card  VIA Apollo CLE266 (integrated)   
Sound Card  VIA VT1616   
Modem  PCTel HSP MR 56K   
Network Card  VIA Rhine II VT6103    
Mouse  Touchpad   
Power Supply  Lite-On® PA-1700-02    
Battery  Sole Energy Corp EM1-410C2

Ubuntu 8.04 will run but you will need to upgrade the RAM.  256MB is not enough.  512MB or 1GB would be better.

---

### Post by ugm6hr on 2008-06-12
> dapper drake was great..........but no longer supported i then found out lol.
Dapper is 6.06LTS - it still has 12 months support.

As for the "slow" aspect - why not try a "light" Ubuntu derivative.

Ubuntulite looks good, Fluxbuntu has its fans too, or create a minimal installation yourself.

---

### Post by Fenris_rising on 2008-06-13
hi guys

beggin your pardon it was edgy eft that ran quick but isnt supported,
dapper drake was just slow.lol

as for ram size, i am for the while stuck with what i have for the for seeable future.

create my own? sounds good but id need pointing at a page or two to get a good grasp of it. Ubuntulite and flux, i will have a look thanks :)
any other suggestions keep em coming please.

---

### Post by housam on 2008-06-13
Try [[COLOR="Red"]_Linuxmini_[/COLOR]]("http://linuxmini.blogspot.com/2007/10/another-linux-mini-distro-berry-linux.html") , instructions [[COLOR="Red"]_here_[/COLOR]]("http://sourceforge.net/project/downloading.php?groupname=berryos&filename=berry-mini-0.80.iso&use_mirror=switch")

---

### Post by Fenris_rising on 2008-06-13
thanks for the heads up there, i will note that one to.
ubuntulite runs into the problem of my ethernet card
being a total *******. ive tried for several weeks following
this that and the other tutorial to get it to work properly
but to no avail. it gets the usual no dhcpoffers that ive seen 
everywhere and unless im missing something it just cant be done
on mine. fluxbuntu hmmmm very nice installed and running.....
had a fight for an hour getting the usb pen drive to be accessable
so i can put the tar.gz ndiswrapper on (its not in the repos) well
that fell over, all sorts of errors (im guessing dependancy's) so i
try in deperation to get the eth port going........no chance. so im
trying to join the fluxbuntu forum........grrrrrrrrr bloody anti-bot
text is playing up but eventually i managed it. just waiting for
the admin to approve me.
Question. what the hell is wrong with ethernet. i have a belkin54g
router. i can look up the dns info on it to tell the laptop where to
look. it is DHCP and its driving me nuts. static ip i cant even fathom if i can set the laptop up as static behind a DHCP router. im not thick
but im beginning to have my doubts. i dont mind working at getting everything going but its been one long slog with the eth port ive tried just about every tut going and its done jack. sorry end of rant i just dont want to go back to windows on the laptop. my PC is pure ubuntu and functions perfectly. someone help me free my laptoppppppppppp.

---

### Post by ugm6hr on 2008-06-13
What do you want to do here?

Not sure why your ethernet doesn't work.  You haven't really given enough information.

If you know what you are doing with ndiswrapper in fluxbuntu - you can install it from the repos - either manually by downloading the deb packages or using nonetdebs.  You don't need the source.

---

### Post by snowpine on 2008-06-13
> **Fenris_rising said:**
> fluxbuntu hmmmm very nice installed and running.....
had a fight for an hour getting the usb pen drive to be accessable


Hi Fenris, to get Fluxbuntu to automount USB devices, try this:

```
mkdir ~/.ivman

```
That should do the trick, let me know if it works.

---

### Post by Joeb454 on 2008-06-13
If you *really* want something that works well, and you want to pick and choose what you want on the system, you could try Gentoo ;)

Or you could try a minimal Ubuntu install :)

---

### Post by Fenris_rising on 2008-06-13
ive installed fluxbuntu to my laptop. what i want to do is get ndiswrapper installed. there is know internet connection at all. i DL'd from source forge the ndis package on my PC and passed it over with the usb pendrive.
i did check the reps on fluxbuntu but ndis isnt in there and i made sure the cd was added just uncase it was on it. as for the eth problem i have just noticed that my connection is PPPoA not PPPoE. i gather from that alone its a problem. i havent found a solution on the forum yet.


> **ugm6hr said:**
> What do you want to do here?

Not sure why your ethernet doesn't work.  You haven't really given enough information.

If you know what you are doing with ndiswrapper in fluxbuntu - you can install it from the repos - either manually by downloading the deb packages or using nonetdebs.  You don't need the source.

 hi m8
well i did it but i think whatever i did to get it connected the first time may have interfered with any subsequent attempts to automate it.
so i fear im going to have to try a reinstall and go from there again.

Hi Fenris, to get Fluxbuntu to automount USB devices, try this:

Code:

```
mkdir ~/.ivman
```

That should do the trick, let me know if it works. 

re gentoo/linux mini

at the rate im going i will have tried just about every type of install going. im not complianing the learning curve is steep when things dont work but shallow when they do.fingers crossed if i can sort out ndis then
that will be the major hurdle sorted. i certianly dont hold anything against linux whatso ever its a learning thing and matching hardware to software can be problematic. the biggest hurdle is my laptop its a generic cheapy made for Dixons sold via pc world so theres no major brand parts in it so im just lucky to have the functionality i do.

---

### Post by Fenris_rising on 2008-06-13
ok reinstalled and tried the ivman. sadly it didnt work so im using the 
pmount /dev/sda1 usb and pumount /dev/sda1 usb in terminal. not the end of the world of course but it would be nice.
i downloaded the common and util deb files for ndis and transferred them to the laptop but i havent been able to open them yet im looking it up now but any help with fluxbuntu would be appreciated.

---

### Post by snowpine on 2008-06-13
> **Fenris_rising said:**
> ok reinstalled and tried the ivman. sadly it didnt work so im using the 
pmount /dev/sda1 usb and pumount /dev/sda1 usb in terminal. not the end of the world of course but it would be nice.
i downloaded the common and util deb files for ndis and transferred them to the laptop but i havent been able to open them yet im looking it up now but any help with fluxbuntu would be appreciated.

Hi Fenris, one possibility is gnome-volume-manager to auto mount the drives. Assuming you are okay with introducing some gnome into your flux! :)

Sorry I can't help with your ndiswrapper problem. I installed it through Synaptic over an already-working ethernet connection.

---

### Post by Fenris_rising on 2008-06-13
ndis is now installed and im just about to try it out after rebooting.
fingers crossed there were no errors in application of the terminal commands. as for gnome, if it does the trick and doesnt slow the sytem down i will try it. tell me more ;)


Success wireless usb is achieved. thats one hurdle out of the way.
DVD commercial disks playing with VLC. big thumbs up so far
web browser is good
email setup
btw im using flux nowwwwwwwwwwwww lolol

---

### Post by ugm6hr on 2008-06-13
RE: USB mounting

What filemanager does fluxbuntu use?

A lighter option than nautilus would be thunar (file manager) and thunar-volman (thunar's mounting system).

I believe that PCManFM (perhaps marginally lighter than thunar) has a mounting function too now - but that might need checking.

---

### Post by snowpine on 2008-06-13
> **ugm6hr said:**
> RE: USB mounting

What filemanager does fluxbuntu use?

A lighter option than nautilus would be thunar (file manager) and thunar-volman (thunar's mounting system).

I believe that PCManFM (perhaps marginally lighter than thunar) has a mounting function too now - but that might need checking.

Fluxbuntu uses Rox as the file manager and ivman for mounting.
Thunar was one of the first things I added. :)
PCManFM is on my "to try" list.
Nautilus doesn't seem "light enough" for Fluxbuntu.

---

### Post by Fenris_rising on 2008-06-13
yep uses rox. im getting on ok at the moment. installed conky but cant find the conkyrc file to edit. show hidden files is on but its obviously not filed away like it is on my PC with 8.04. syntax of the CLI is a little different thats thrown me a bit. but overall if it stays this good im very happy at the moment. up to my nexk in ubuntu :) i will have a look at your suggestions re usb mounting thanks.

---

### Post by snowpine on 2008-06-13
Hi Fenris, just a little more information on the file manager/volume mounting thing. Maybe this will help you out.

Nautilus is the default file manager of Ubuntu, so it depends on certain Gnome-related packages. Thunar is the file manager for Xubuntu, so it has some Xfce dependencies. 

The whole point of Fluxbuntu is that it uses Fluxbox instead of Gnome or Xfce (or KDE, which is what Kubuntu uses). This is why it works well on very old computers; Xfce and especially Gnome are somewhat "bloated" compared to the slimmed-down packages they chose for Fluxbuntu. 

So, let's say you want to install Nautilus. When you mark it for installation in Synaptic, it will tell you it needs some other Gnome-related packages as well. 

Unless you have an ancient computer and you need it really bare-bones, there's no real problem with installing Gnome or Xfce stuff. In fact, once you've installed those basic packages, you can start using other applications that depend on them. It may even be that you've already installed them without realizing it based on other applications you've selected! As a general rule, I would choose either Xfce, Gnome, or KDE and stick with it. In other words, if you have already installed Nautilus, and are thinking about installing a new KDE application, ask yourself if there is an equivalent Gnome application that works just as well. 

gnome-volume-manager will automount your drives, and it is a good choice if you decide to install Nautilus and its gnome dependencies. thunar-volman is the Xfce equivalent, and it is a good choice if you install Thunar and its related packages. Or you can keep experimenting with Rox and Ivman, keeping your system nice and slim for the time being! :)

One other tip. There is a file called ~/.fluxbox/startup where you can list any programs you want to automatically load. So for example, you could add

```
gnome-volume-manager & 
```

to automatically boot the volume manager (the '&' at the end of the line is important).

Good luck and please share any tips and tricks, because I am a beginner with all of this too!

---

### Post by snowpine on 2008-06-13
Hey, one other thing I forgot to mention that's kind of important. If you are running something like Nautilus, use this syntax:

```
nautilus --no-desktop
```

Otherwise, it will try to set your wallpaper and turn your Fluxbuntu into mini-Ubuntu! :)

---

### Post by Fenris_rising on 2008-06-13
hey there

thanks for the that dirth of info m8. very helpful indeed. what i will do is try and learn flux as is first. there are certain things im finding difficult but i think thats down to my small knowledge of commandline. i know enough on ubuntu 8.04 to get by and set the odd bits and pieces up. i have dual booted the laptop with its original XP but given a larger portion of the drive to flux whilst i learn its fiobles. however i think your info as regards putting gnome in with all its benefits is very tempting and may make my life easier and perhaps as flux is already slimmed down it wont adversly effect the smooth fast action of the OS. the laptop is about 4yrs old so not to bad and if it can run XP it should be able to run linux as well if not better. i think the problem is mainly the laptop itself being a budget type so its just tweaking and changing the linux OS so that it has all the functionality i need, plus a little bit. it is already faster than the XP os. one thing i have to learn is getting icons and adding to menus in flux. i cant remember what i installed earlier but it installed firefox as well for dependancies. i knew enough to type firefox in the CLI to open it up but there is no icon for it or a menu entry. once i get approved by the admin on flux i will be able to study and question in their forum as well. i absolutely am 100% so bloody glad i have moved over to the linux OS, even with the learning curve i know i have a far superior OS and the customer srvice is so much better. :lolflag::lolflag::lolflag: if i get stuck gnoming the install i know where to come.

cheerssssssssss (ticked the thanks medals btw)

---

### Post by snowpine on 2008-06-13
Well cheers right back at 'cha. 

Here is a little guide I wrote to getting started with fluxbox menus: 

1.  Create a backup of the menu in case things go awry:
```
cp ~/.fluxbox/menu ~/.fluxbox/menu.backup
```
2. Open the file for editing (note most people would suggest nano but I like Abiword for this due to its copy/pase and find/replace features):
```
abiword ~/.fluxbox/menu
```
3. Press Ctrl+A to select all
4. Press Ctrl+C to copy
5. Move the cursor to the beginning of the last line that says [end]
6. Press Ctrl+V to paste (nesting a copy of the entire menu within itself)
7. Scroll up to the middle of the document to the second instance of [begin] and change [begin] to [submenu]
8. Scroll to the bottom and add a new line between the two instances of [end]:
```
[exec] (edit this menu) {abiword ~/.fluxbox/menu}
```
9. Press Ctrl+S to save.

Now, right, click and you should have a slightly different menu (if not, go to Fluxbox and choose Reconfigure). Basically we've done two things: 1) we put the default menu into a submenu so that it is always accessible as we make changes to the new menu; 2) we made a link to easily edit the menu file. So you can start to mess with the first half of that file, for example by adding your favorite applications to the root menu!

---

### Post by Fenris_rising on 2008-06-14
hi m8
thanks for that. i will give it a whirl. i just noticed your in the fluxforums to lol. im still waiting for admin to approve my application.
turned laptop on this morning and it all works still yayyyyyyyyy! lol
heres a question for ya. where is the .conkyrc file kept on flux? on 8.04 i can find it with my eyes closed, im assuming the file system is organised slightly differently.

---

