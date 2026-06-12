---
title: "Asks me to login on boot!"
date: 2008-02-06
forum: Hardware &amp; Laptops
---

### Post by ningall on 2008-02-06
While looking at the boot screen as its loading modules and mounting drives etc it hangs at

nathan-laptop@login

If i enter my user and pw it goes through but i still have to login to the interface

If i leave it it stays there for 5-10 seconds then carries on booting but sometimes it doesn't even do it but i do notice when it does happen the system runs a lot slower


Im gonna try and see what causes this to come up and narrow it down but if any one has encountered this and fixed it give me a shout

I have an Asus X50RL

[http://www.ebuyer.com/product/134523](http://www.ebuyer.com/product/134523) for system specs

I am on ubuntu 7.10 dual booted with win XP pro

---

### Post by ningall on 2008-02-06
OK ive done some testing and IF i have my ethernet cable plugged in and connected to my router this login thing does not come up at all and boot is much quicker

My prefered connection at home is a Wireless one setup to use a static IP and a WPA passphrase

I am using the Madwifi drivers an on Atheros AR5007 which works at home and at uni where i have to change to roaming mode

Anyone have any ideas?

---

### Post by ningall on 2008-02-06
OK i think its due to me having a Static Ip for my eth0

I only use the Wired Connection at home and do not want to have to renter my details everytime i need to connect its not worth the slow performance in the OS 

I am going to set it back to roaming and reboot and see if that helps

---

### Post by ningall on 2008-02-06
OK i set it back to roaming mode and to no avail the login message still appears it looks like i need to have an Ethernet cable plugged in for everything to run fine which is a pain as i cannot do this at university were everything is wireless and i use ubuntu for programming  in netbeans

anyone help as this is a seriously annoying problem

---

### Post by Helgiks on 2008-02-06
If you only use it on one place, you can of course try to  disable the ethernet in the bios, and than when you intent to use it turn it back on + that saves you some battery power.

---

### Post by ningall on 2008-02-06
yeah but i might need it in though thats the problem

thanks for the tip though ill use it as a last resort 

Still needs the Ethernet connected to run fast and boot properly

---

### Post by ningall on 2008-02-06
[IMG]http://img222.imageshack.us/img222/5770/photo0008np3.jpg[/IMG]
is a photo of where it hangs

---

### Post by ningall on 2008-02-07
still suffering from this problem

---

### Post by bwtranch on 2008-02-07
Checking minimum space in /tmp...

A person would have to ask, why?

---

### Post by bwtranch on 2008-02-07
Once you login, do you ever get past runlevel1? or are you just stuck with a CLI?

---

### Post by ningall on 2008-02-07
after the login CLI comes up i can leave the machine idle for 10-15 seconds then gnome loads up and the boot completes and i can login normally

If i login on the CLI it says welcome to Ubuntu etc then gnome loads up normally and i have to login again through Gnome

I have removed network manager in favour of wicd as similar problems have resolved by this but unfortunately not me

can i also state that system performance is also poor when a network cable is not plugged in

---

### Post by ningall on 2008-02-07
[IMG]http://img207.imageshack.us/img207/6919/gutsy200802074fi2.png[/IMG]

---

### Post by ningall on 2008-02-07
Ok ive have fixed this issue

I removed network manager
Installed Wicd
Change /etc/network/interfaces so that only 

```
auto lo
iface lo inet loopback
auto eth0
auto ath0
```

Now it boots straight through no problems with the network cable unplugged and auto runs the wireless connection tray icon

SOLVED

---

### Post by Yellow Pasque on 2008-02-07
If it's the eth0 that's really holding you up, try turning off the auto-link in /etc/network/interfaces. Comment out the 'auto eth0' line. Then, whenever you do plug in to the network, type this to bring the link up:
```
sudo ifup eth0
```

EDIT: LOL, I was a few minutes too late :P

---

### Post by ningall on 2008-02-08
thanks anyway though i think i tried that at one point but all is dandy now jsut need to find out why thr grub loader is so slow to load and get me my OS list

---

### Post by a Hunt3r. on 2008-02-15
my Asus X50RL has a built in wireless connection and when i disconnected my ipod from my comp my wireless adapter thingy atomatically turned off and i cant turn it back on coz the icon on the toolbar isnt there  :mad:
plz reply or send an email to [email]xbass_hunt3rx@live.com.au[/email]

ps: i have an  wireless router

---

