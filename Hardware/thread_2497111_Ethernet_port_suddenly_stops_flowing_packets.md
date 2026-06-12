---
title: "Ethernet port suddenly stops flowing packets"
date: 2024-04-23
forum: Hardware
---

### Post by normlewis on 2024-04-23
This is a two week old OrangePi 3B board.

I was working away when all of a sudden, network connectivity ceases. I figured I'd done something wrong so looked at everything but it's all correct. 
The link/carrier is up, the IP is manually configured, route is correct but no network access. 

I of course changed cables, connected to different switches, still no network access outside of the board. 
I rebooted, even re-installed a couple of different OS versions and nothing. 
The frustrating thing is that I can see what appears to be Ethernet traffic, the LEDs are flashing as if traffic is flowing but nothing is. 
I've tried manually setting and DHCP by the way.

It's connected to a good power source with 5amps so it can use what ever it needs.
No errors in the logs, dmesg looks normal, what's going on?

I've only had the board for two weeks and never seen anything like this where everything is correctly configured but simply no package flow.

Anyone have any thoughts on this? Are these boards reliable or not?

---

### Post by TheFu on 2024-04-23
> The link/carrier is up, the IP is manually configured, route is correct but no network access. 

Since this is your first post here, rather than making claims, please "prove it" with posted configurations and current settings. Hard to prove you swapped cables and ports, but I'll beleive that.  Network configuration issues, especially manual, for people not used to doing it are common.

When posting, show the commands used AND the output unless it is more than 20-50 text lines.

Whenever posting here, please, please, please, use forum 'code tags' and text, so we can see what you see on the terminal with the correct columns.

The **netplan.yaml** file contents would show the configuration.  The **netplan generate** and **netplan apply** commands + output would be helpful too.

```
$ ip r
$ ip a
```
will show the results for the NIC. That's an example of the 'code tags', BTW. Columns will be maintained as pasted (assuming you use select/paste) to put all the text into a forum edit entry box.

OT: 
As with nearly all hardware, blanket statements about any specific brand or model show just 1 person's experience, not necessarily the experience of 1M+ people who didn't have the same issue.  For example, I won't buy any more Seagate storage devices, because of my history with the company.  Yet, they are still in business and appear to be doing fine without my 1 HDD/year purchase.  Seems completely crazy to me, but I don't expect the people who haven't had the same experience to have the same feelings about their products.

---

### Post by normlewis on 2024-04-23
First post here, not new to working with computers. Been working on them since the 80's. 
Been using Pi and embedded hardware for well over ten years.
Normally, I would share the commands and the outputs but in this case, hard to do since there's no network access and I would have to manually re-write everything on the screen that is shown. 

No blanket statements and I have not dissed the manufacturer, nor did I simply post without trying anything but the key take away should be, I've tried everything I can think of, does anyone have any other thoughts because I think the Ethernet has failed at this point. Odd that I can see link activity when there is no network access.

PS: To be safe, I also used arp to set an IP from the LAN side to the MAC of the board to see if I could ping it but it cannot be reached.

---

### Post by #&amp;thj^% on 2024-04-23
Seems to be a common problem for that board, maybe have a peek here::[https://old.reddit.com/r/OrangePI/comments/1aojmn3/orange_pi_3b_ethernet_doesnt_work/](https://old.reddit.com/r/OrangePI/comments/1aojmn3/orange_pi_3b_ethernet_doesnt_work/)

The post by yoniyang shows promise.

Good Luck

---

### Post by normlewis on 2024-04-23
Thanks [**[COLOR=#000000]1fallen[/COLOR]**]("https://ubuntuforums.org/member.php?u=2040855") I had not found that. 
Makes me a bit nervous as I cannot afford failures once they leave the shop.

---

### Post by #&amp;thj^% on 2024-04-23
> **normlewis said:**
> Thanks [**[COLOR=#000000]1fallen[/COLOR]**]("https://ubuntuforums.org/member.php?u=2040855") I had not found that. 
Makes me a bit nervous as I cannot afford failures once they leave the shop.

I understand that fully, I wish I had that board to experiment with, but sadly I don't.

Please keep us updated with any success and or failures.

edit:  Also good documentation found here as well: [http://www.orangepi.org/orangepiwiki/index.php/Orange_Pi_3](http://www.orangepi.org/orangepiwiki/index.php/Orange_Pi_3)

---

### Post by The Cog on 2024-04-23
I would be inclined to use tcpdump to see if the board can see any incoming packets, e.g.: **[FONT=Courier New]sudo tcpdump -i eth0 -ln[/FONT]**
tcpdump should also show packets leaving using arping in a different terminal even if it's deaf, e.g.: **[FONT=Courier New]sudo arping -I etho 99.99.99.99[/FONT]**

---

### Post by #&amp;thj^% on 2024-04-23
I would also try a USB Ethernet device, not the desired method but.....

I've talked with some other testers and they claim that ether port only works on kernels 5.4, and they did not have any nice words for that board.

---

### Post by TheFu on 2024-04-23
> **normlewis said:**
>  Normally, I would share the commands and the outputs but in this case, hard to do since there's no network access and I would have to manually re-write everything on the screen that is shown. 
 

I'd use file redirection to place the the results into a file, then use a USB flash drive to copy off those files. [https://linuxhandbook.com/redirection-linux/](https://linuxhandbook.com/redirection-linux/)   I'm a huge fan of the '**tee**' tool. But you can feel free to do things another way, if you like.  

```
ip a | tee /tmp/log.ip-stuff
ip r |  tee -a  /tmp/log.ip-stuff
cp  /tmp/log.ip-stuff /mnt/usb-flashdrive-location/
```

This simple things are often what we miss. It is the human thing to do.

Good luck.

---

