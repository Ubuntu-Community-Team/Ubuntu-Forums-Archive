---
title: "Wifi signal strenght Atheros card edgy"
date: 2006-11-23
forum: Hardware &amp; Laptops
---

### Post by ranpha on 2006-11-23
I upgrade to edgy and i noticed that all my wifi connection are cut i  half. I tried to connect to my own Ap. 40% signal strenght. I use gnome network manager to connect to my network.

With dapper my signal strenght was 80%. Also under edgy i got a lot of disconnects even when 1 meter from my AP.

Any one else have this problem? and how to solve it?

---

### Post by Rontie on 2006-11-28
yeah i just experienced similar issue myself running edgy (install two days old)

have ATI atheros card
madwifi for driver


I have been surfing for two on this new install and everything has been working fine. Sent an email using evolution, went to smoke a cigarette and when i came back i had no Internet, and my signal strength was spastic

I logged into XP and everything was working fine full signal strength and connected. In edgy, I tried all my settings using Gnome network manger, and used wifi radar and nothing. It said it could see the router (Xanadu) but could not acquire an IP address.

Solution: I went in and made everything static and suddenly it worked.

can't image why it wouldn't like obtaining the ip automaticly but it didn't. Would really love to know why and how to fix...

I wonder why is going to happen when i try to connect to another network where i don't have the option to be static?

Any advice would be great... thanx

---

### Post by xyzzys on 2006-11-30
I have the same problem... It seems to be a bug of the new Ubuntu Edgy...

(Excuse my very poor English :P)

---

### Post by spotman on 2006-12-08
not sure if anyone else is still battling this..

i just upgraded one of my machines to edgy, which has an atheros (madwifi) chipset, and I am experiencing the same problem.  I can only get about 20 % reception, and the router is 6 ft away.  In dapper I could get full reception without problems.

on my laptop, which has an intel wireless chip (and is running edgy), I get 95% reception.

what is weirder yet, is that some of my neighbors base stations have way better signal quality according to the graphs, which is certainly not accurate.  my laptop actually displays my neighbors as less, which is accurate.

---

### Post by xemvip on 2006-12-08
FWIW, according to dmesg my wifi card is "Atheros 5212", according to the sticker on the back of the card it is an AT&T Plug'n'Share 6700G.

It works perfectly under Edgy.  I don't know anything about madwifi though?  :-k 

So maybe that info is pointless?  I  just figured it might be helpful to know that SOME Atheros cards work properly.  :p

---

### Post by spotman on 2006-12-08
yeah mine is also a 5212...

no idea why its being weird.  I've tried all channels and options my router has on it.

---

### Post by aleksabl on 2007-01-11
Hi,

I'm having the exact same problem here. We have to computers side-by-side, one (a laptop with Intel Centrino chipset) shows a quality of about 80-90, but the other (having a AR5212 card) shows something between 15-25. I've checked to see that the numbers reported by ifconfig are in fact correct, by looking at the signal rate at the Access Point. I've also tried setting the AP just 1/2 meter away from the computer and the signal quality was still way too low (maybe out 50).

This seems to be a problem with the madwifi-driver: [Madwifi #663]("http://madwifi.org/ticket/663") . If nobody has submitted a ticket to the Ubuntu Launchpad, I'll probably do it later this day.


Aleksander

---

### Post by aleksabl on 2007-01-11
The bug has already been reported: [https://bugs.launchpad.net/ubuntu/+bug/66481](https://bugs.launchpad.net/ubuntu/+bug/66481)

---

### Post by Gohalien on 2007-04-29
Looks like my problem is the same as all in here...

---

### Post by aleksabl on 2007-04-29
The same problem exists in Feisty too.

---

### Post by teachop on 2007-04-29
This also happened for me, very low signal and constantly disconnect / reconnect, even right near the wireless router.  My laptop is an acer aspire 3100 with the Atheros wifi built-in.  Based on some other posts, I disabled the Network Manager in System> Preferences> Sessions, and set up using System> Administration> Network.  After doing this, I ended up with a signal of 90%, and no more constant disconnect / reconnect.  It works great, except I had to drop back to WEP from WPA because I didn't know how to select that option.  All good, BUT...

I took my shiny new linux machine to work to show off a couple days ago, changed the wireless settings to get it to work there, and after I came home, I had to go around and around before I finally held my mouth right and booted and it worked again.  I am sorry I cannot report the exact sequence, but it was close to this:  Turn Network Manager back on; get wireless working; disable Network Manager and reboot; goof about with the settings in System>Administration>Network; reboot.  It works now.

Now I cannot roam, and am totally in fear of touching the wireless settings again.  But it is working fine.

---

### Post by ThinkBuntu on 2007-05-24
I filed a ticket with Madwifi. This is a driver bug, and has very little to do with Ubuntu.

---

### Post by dyrer on 2007-05-24
Atheros has released new madwifi drivers.
How can use them to feisty

---

### Post by teachop on 2007-06-02
I too would like to know how to use the new drivers in Feisty.

I spent a week on Vista (blech) and now am back on Ubuntu.  This time I am being more careful about what I tweak in Feisty.  I don't want to dump Network Manager this time, because I want the roaming ability.  But unfortunately right now I am using a cable because wireless keeps disconnecting.

By the way, when I ran Vista on this laptop last week, after the install, Windows updated the Vista Atheros driver too.  I really hope we can use the new Madwifi driver somehow.

---

### Post by zergberg on 2007-06-02
Where is this new driver?

---

### Post by teachop on 2007-06-03
The thing that puzzles me about the problem being in the driver, is that the driver works great if Network Manager is not involved, including how the Network Monitor applet shows a reasonable signal value.  I have used WEP and now WPA and have no random disconnects or weak signal shown.  I guess that means that the problem is in how the driver supports roaming?

---

### Post by tturrisi on 2007-06-03
Madwifi is a good driver & has few bugs.  Networkmanager is the problem, not madwifi, it's a buggy app.
The signal level reported by madwifi driver is really not so much a bug as it is differences in how different drivers/apps calculate the signal levels.  Rule of thumb is just ignore reported signal levels unless the connection does not work at all.  It you can connect to an ap and use it then reported signal levels are moot.

---

### Post by moeFinley on 2007-06-06
I have the same problem with my Thinkpad T41.  If the network is open it doesn't seem to have a problem.

---

### Post by moeFinley on 2007-06-08
I've just switched to Kubuntu on the same laptop and I have the same issue.  I'm not sure what's shared between Ubuntu and Kubuntu but that must rule out Network Manager?

---

### Post by NotReallyIntoPokemon on 2007-06-08
So, it is not Network Manager, not the drivers, and not Ubuntu.  This is not looking promising.  Recently I decided I'd try out this Linux stuff all the kids are talking about nowadays and decided I would go with Ubuntu, which was supposed to be devastatingly easy!  Imagine my dismay.  I, too, have Atheros Wifi, and by inputting some crazy command into the terminal I can further specify that it is an "AR5211".  It seems that having the internet is a prerequisite for doing most anything, especially on Linux.  So, until I can get this working, it is basically just a nice startup noise for me.

In any case, I disabled the Network Manager, and I must not be holding my mouth right yet because that has no effect for me.  How many of you others have gotten it to work doing that?  Is there anything I can try in the meantime?  Most importantly, this problem seems to be vague, so where should I be looking to keep tabs on how soon it is to being a fix?  Is there anyone actively working on this issue?  Thanks tons.

---

### Post by moeFinley on 2007-06-10
Wahoo! it's working!

I've install MintLinux and all seems to be working perfectly :)

I don't know what the difference is?  MintLinux is pretty much Ubuntu Feisty with a few updates and extras.

I'm going to keep testing it to make sure it is really working 100% all the time and then I'll have a closer look at what could have made the difference.

---

### Post by scales on 2007-06-14
i definately would like to know if it works.  i am having the typical issues and would like for things to be solved.

---

### Post by moeFinley on 2007-06-14
I haven't had time to look in to why but it works.  I've been using it almost a week now and I've had no problems.  The signal still seems a bit low but maybe this is accurate, I don't have anything to compare.  But it doesn't seem to make a difference to the speed.

All I really care about is it doesn't disconnect!

---

### Post by teachop on 2007-06-14
I was wondering now that you have it working well, are you using Network Manager in Mint Linux?

---

### Post by moeFinley on 2007-06-15
Yes it still uses network manager (NetworkManager Applet 0.6.4).  Is that a later version than the one in Feisty?

---

### Post by teachop on 2007-06-15
I believe that is the same version, Feisty repo says: 0.6.4-6ubuntu7.

I tried the Cassandra Linux Mint live CD, and it didn't pick up the wireless hardware.  I only had the "Wired" option so not sure that will work out on this laptop.  I guess I will stay with Feisty.  The setup I have now on Feisty is functioning (wpa-supplicant + madwifi, disabled NM) including reliable resume from suspend.  The thing I don't have is roaming.

---

### Post by clar2391 on 2007-07-11
I just installed Ubuntu 7.04 on an Intel Mac Mini, and I have the same (or similar problem).  The reported signal strength is very low, 35% - 40%, and I am unable to connect to my Linksys router unless I turn off roaming and broadcast my SSID.

Any fixes in sight?

---

### Post by moeFinley on 2007-10-20
I'm using Gutsy (7.10) now and there are now WiFi problems on my T41.  Ubuntu rocks :)

---

