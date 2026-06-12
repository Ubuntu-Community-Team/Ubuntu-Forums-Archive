---
title: "Acer Aspire One, No wifi"
date: 2009-03-29
forum: Hardware
---

### Post by ephigy on 2009-03-29
Ok I tried everything before posting, and I'm completely stuck. I've been without wifi for two or three days now and I have no clue as to why because it worked fine before then.

I installed ubuntu on my aspire one as per the instructions on the page in this forum: [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

basically running on madwifi

And it worked!


But somehow something went wrong and I'm not sure what.

When I enter sudo lshw -C network I get the following:

*-network DISABLED

No wireless networks appear anymore in my connections menu

I tried installing the windows driver using ndisgtk but that didn't work so I uninstalled it. 

Any ideas? Need more info?

---

### Post by s.dalas on 2009-03-29
have you tried to add the wireless connection manually?
check this out it might help : [http://ubuntuforums.org/showthread.php?p=6966293#post6966293]("http://ubuntuforums.org/showthread.php?p=6966293#post6966293")

---

### Post by ephigy on 2009-03-29
I just tried again both Connect Hidden Wireless Network and Create New Wireless Network, but both seem to time out. I get a Disconnected from Network message, but it never actually connected. I used to see at least three networks before this problem arose, now I don't see any wifi connections listed.

---

### Post by s.dalas on 2009-03-30
try to reinstall network manager. if you are using gnome go to synaptic and reinstall network-manager-gnome and network-manager .
if you are using kde you need network-manager-kde and network-manager

---

### Post by rodneymillerpca on 2009-03-30
I just experienced that with a Acer Aspire 4520. This helped me perfectly in less then 15 minutes "http://www.hp2133guide.com/forums/viewtopic.php?p=10230". See my notes at the bottom of that post.

---

### Post by ephigy on 2009-03-30
Ok I did everything in that tut, but the result is the same. No wifi listed and sudo lshw -C network still lists *-network DISABLED.

---

### Post by ephigy on 2009-03-30
I just reinstalled network-manager and network-manager-gnome nothing changed.

I reactivated my hardware drivers to see if that would help sinc the other tut didn't solve my issue.

there are two listed:

Support for the 5xxx series of Atheros 802.11 wireless LAN cards.
Support for Atheros 802.11 wireless LAN cards

the first one show "This drive is activated but not currently in use"
and the second won't activate "this driver was just disabled, but is still in use"

I'm not sure it's really in use as it was disactivated and when I tried to activate it that's the message I get.

my ath_pci is blacklisted from the previous tutorial.

I'm really puzzled especially sinc it once worked really well.

---

### Post by ephigy on 2009-03-30
After rebooting the first drive is listed as being in use, but I still get *-network DISABLED as mentioned above.

---

### Post by ephigy on 2009-03-30
Anyone have any idea? It seems I'm tried everything and I'd rather not reinstall just for the wifi. None of the drivers seem to work. I looks as though I have no wifi when trying to scan.

I've been without wifi for 4 days and although I'm starting to learn a lot, I'm still clueless as to how to get it working again.

Let me know if I can provide more info that can be usefull

---

### Post by pewterbot9 on 2009-03-30
I don't own the Acer, but the Asus eee PC 1000 HA, and could not get wifi to work with Ubuntu 8.10. Madwifi, NSDI wrapper, just did not work. Finally, I discovered Eeebuntu, and it recognized my Atheros wifi right off the bat. 

[http://www.eeebuntu.org/index.php?page=download]("http://www.eeebuntu.org/index.php?page=download")

---

### Post by ephigy on 2009-03-30
I'll keep that in mind if it comes down to that, but I'd really like to save the setup I have now before going through the hassle of reinstalling everything.

I've been reading a little bit on a forum dedicated to the acer aspire one and it seems that this is a widespread problem. wheter you're using linpus, xp or ubuntu. I'm starting to think it might be a hardware problem. or is it... I'm still confused!

---

### Post by RockDoctor on 2009-04-02
Perhaps a dumb question, but did you update your kernel or NetworkManager between the time wifi worked and the time it failed? I'm using the latest kuki kernel; it works well for me and I've locked that version to prevent updating

---

### Post by tarps87 on 2009-04-02
Have you moved the wifi switch?
When I first installed Ubutnu on my Acer one I acidently turned it of and had to boot into the limpus partition to work out if it was on. Since the latest version of the madwifi drivers the wifi switch works in Ubuntu, also with this version of the madwifi driver you can make the L.E.D's work.

---

### Post by ephigy on 2009-04-02
I got it to work again after uninstalling the windows driver. It took me a while to figure it out but I think it has to do with suspend mode. I used that a lot and it seems the drivers don't work after coming out of suspend. 

I'm using the .7 kernel as the .11 broke my LAN and WLAN!

Is it worth it to install the kuki kernel? And how would I go about doing that?

---

### Post by Sprut1 on 2009-04-02
> **tarps87 said:**
> Have you moved the wifi switch?
When I first installed Ubutnu on my Acer one I acidently turned it of and had to boot into the limpus partition to work out if it was on. Since the latest version of the madwifi drivers the wifi switch works in Ubuntu, also with this version of the madwifi driver you can make the L.E.D's work.

I thought the same thing, as far as I know the switch works, but doesn't give any feedback. Gave me some troubles.

---

### Post by tarps87 on 2009-04-02
I used the same instructions as you to set it up using the madwifi drivers and didn't have any problems with the latest kernel, there is also a solution for suspending on there. From the look of it the kuki distribution uses the standard kernel although they may have applied some patches

---

### Post by beefcurry on 2009-06-01
tried the launchpad bug report method of using backports and modprobe ath5 but nothing works, I guess I'll have to just reinstall and NEVER NEVER NEVER update or suspend.

---

### Post by ianmillington on 2009-06-02
> **beefcurry said:**
> tried the launchpad bug report method of using backports and modprobe ath5 but nothing works, I guess I'll have to just reinstall and NEVER NEVER NEVER update or suspend.
What ubuntu version are you running? We got an aspire one 110 last week and installed UNR9.04 on it and wireless works out of the box.

---

