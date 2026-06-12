---
title: "Help with Gateway M-1626 wireless internet"
date: 2009-03-18
forum: Hardware
---

### Post by sargeant dread on 2009-03-18
I'm currently running either Ubuntu 8.10 or Kubuntu 8.10 and in both cases in order for me to surf the internet or update I need to have a very strong connection. I can't be more than 15 ft. away from my wireless router in order for it to work properly. This is a large problem because at school I live on the 7th floor so I can't even get close to our wireless router. I'm using a Gateway M-1626 and the only information I could find about my wireless card is "Integrated Realtek 802.11b/g Wireless Networking (CRU/EURP)". Do I need an additional driver or something?

---

### Post by gatordude on 2010-04-30
I have the same problem. I am adding Ubuntu to my nieces laptop (Gateway M-1626) and on the first install the wireless connection was fast. I could be anywhere in the house and have >50Mbps. While tweaking the xorg.conf I muffed up the install and spent more time than I wanted to on fixing it so I just reloaded Ubuntu 9.10 and now I am lucky to get >10 (usually 1 to 6Mbps) anywhere in the house. This laptop (Gateway M-1626) gives me >48M in Vista so I know the card works fine.

nm-tool shows that I have the rtl8187

Does anybody know if there are different default drivers that could get installed? If so is there a way to choose between the ones available?

Its not my wireless router because I am on my main (ubuntu 9.10) machine which uses a USB D-Link module and it is >300Mps and my windows/Ubuntu laptop (Dell 600M) works fine >128Mps.

I am currently running through this [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#manual]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#manual")
to see if there is any information on that page that may help.

---

### Post by gatordude on 2010-04-30
Arrrrgggggghhhhhh!

My Dell 600M has an Intell 2200BG wireless chip and the Gateway M-1626 has the Realtek rtl8187b.

Here is all the information needed to either help or make you go out and purchase a USB dongle and use the Windows Wireless application because it doesnt look good for people that have this chip because they will have their work cut out for them to get it fully functional.
Here is the information if you have not found it yet.
[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b]("https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b")

Am going to give all of that a whirl after dinner.

I went ahead and loaded 10.04 on it and it still has the same problem.

Cheers

---

### Post by steve161 on 2010-05-01
I'm have the rtl8187b card and my wireless connection is not recognized.  There is a bug report filed so hopefully it will be corrected soon.  My temporary fix is to install the 2.6.31.12 kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/") and boot into that when I need a wireless connection.  There are some error messages when booting with this kernel, but it seems to otherwise run well.

---

### Post by gatordude on 2010-05-02
Bugs! We need a bigger boat!

It seems that bug has been around forever. So...

I sent an email to Realtek (dont laugh) and asked for the drivers.

OK, now you can laugh.

I have a thought. Would the Windows Wireless app work with the .inf and .sys files extracted from Vista? Of course the current driver would have to be disabled but would it work? I am not a pro on embedded devices and intricacies of the inner workings of the kernal but I would welcome some thoughts.

The laptop I am working on does have a copy of Vista 64 so if  I could track down the files needed and if (big IF) it wouldn't damage the chip I would try it.

---

### Post by gatordude on 2010-05-03
Woke this morning with a wild hair and am searching for how to disable the driver for rtl8187b and am going to give the windows wireless app a try.

Ummmmm after searching for a bit, how do I do that?

---

