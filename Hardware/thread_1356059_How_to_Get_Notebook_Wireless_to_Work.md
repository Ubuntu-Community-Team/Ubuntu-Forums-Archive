---
title: "How to Get Notebook Wireless to Work?"
date: 2009-12-15
forum: Hardware
---

### Post by oldefoxx on 2009-12-15
This is proving to be really hard to get done.I've worked with and on PCs for a long time, but never tried to do wireless before.  It was not allowed on company PCs, meaning laptops had to be plugged into the network when us were in the office, and many had to employ encryption devices as well.

That said, this is what I have:  A Tolshiba Satellite L355-S7915 17" wjth both a wired and wireless adapter.  From what I can make out with the info online, the wired adapter is a Realtek 8101E/8102E PCI Fast Eithernet Controller, and that is working fine for my wired connection.  Using lspci -v | less, then lsusb -v | less, I was able to determine that the wireless adapter is a Realtek 8189.RLT8187B USB to LAN Controller.  Further checking online is that you can use ntdswrapper and a Windows driver with some limited success before Ubuntu 9.04, but for 9.04 and 9.10 there is built-in support for the Realtek controller.

Can't prove it by me, but maybe that is because I'm into something that I'm not clear about.  Several articles or posts have stated that the wireless worked right out of the box, yet I havde nothing to show for my efforts.  It took me a couple of hours just to find out where the Network Manager was, and then it gave me no option for adding any other driver, even if I had known which one to add.  I might add that I tried this with both Ubuntu 9.04 and 9.10, with the same results -- nothing. There was even a claim that you could even use a Windows driver and the ndiswrapper,
but reading a source about ndiswrapper, it does not appear that this adapter has been tested and found to work in this fashion.  It was not even apparent that any Realtek adapters had been tested under ndiswrapper.

Another question then is whether this wireless connection can only be used with a private network, where you have to have assigned IP addresses and things like the SSID and password, or if it can be used in a shared network, like at a local fast food place with its own wireless hotspot.  And of course, how you go about setting it up for places like this.  Heck, how do you get signal bars on your screen?

If you've done anything ng along these lines and had good results, would you please explain exactly what it is that you did?  It could be a big help.

---

### Post by coffeecat on 2009-12-15
> **oldefoxx said:**
> Several articles or posts have stated that the wireless worked right out of the box, yet I havde nothing to show for my efforts.  It took me a couple of hours just to find out where the Network Manager was, and then it gave me no option for adding any other driver, even if I had known which one to add.

Stop right there a moment! :) If that Realtek chipset works out of the box - I wouldn't know because I do not have experience of that chipset - then you don't have to add a driver. And you certainly wouldn't have to worry about ndiswrapper.

Assuming you haven't already installed ndiswrapper - please tell me you haven't installed ndiswrapper! - what happens when you simply click on the Network Manager applet icon? Can you see your wireless network listed? If you click on your wireless network, are you prompted for your passkey? Or if an unsecured network, does it connect?

If that chipset really does work out of the box then the kernel driver for it will be autoloaded for you. Then all you have to do is the above. Right-click on NM and make sure 'enable wireless' is ticked.

I'm logging off now - late here - but good luck! I'm sure someone will be along in a moment with a whole load of terminal commands. :p

---

### Post by oldefoxx on 2009-12-15
Well, to answer the questions, the Network Manager is this small icon that appears somewhere on the right side of the upper tool bar.  If I have a wired connection in place, it shows what looks like a monitor imposed in front of another.

If I right-click on the icon, it shows a number of choices, from Enable Networking and Endable Wireless to Connection Information and Edit Connection, then finally About, which shows you your active connection (if you have one).

In my case, the connection information is about the wired connection, identified as Auto eth0.  Though Wireless is enabled, the only thing that shows up is the wired.  After a left click, I see choices for wired and wireless network(s), VPN connections, and options to connect to an hidden Wireless netork or Create New Wireless Networks.  If I disable or disconnect the wired network, the displayed icon changes to four bars, and I get a blue circle drawn as it tries to establish a connection by wireless.   It might come back and say I made a connection, but Firefox keeps showing me that I'm really not connected anywhere.  There is no place I know to look to see something like Auto wlan0, which I assume is indicative of a wireless connection, or even any confirmation of what driver is being used to access the USB to LAN Adapter known as RLT8187B.

So what am I missing here?

---

### Post by coffeecat on 2009-12-16
> **oldefoxx said:**
> In my case, the connection information is about the wired connection, identified as Auto eth0.  Though Wireless is enabled, the only thing that shows up is the wired.  After a left click, I see choices for wired and wireless network(s), VPN connections, and options to connect to an hidden Wireless netork or Create New Wireless Networks.  If I disable or disconnect the wired network, the displayed icon changes to four bars, and I get a blue circle drawn as it tries to establish a connection by wireless.   It might come back and say I made a connection, but Firefox keeps showing me that I'm really not connected anywhere.  There is no place I know to look to see something like Auto wlan0, which I assume is indicative of a wireless connection, or even any confirmation of what driver is being used to access the USB to LAN Adapter known as RLT8187B.

So what am I missing here?

You've done almost all the right things, but it confuses the issue leaving the wired connection in situ. Unplug the ethernet cable, left-click on the NM applet icon and select your wireless network. If it prompts you for a passkey, put this in. Once it says that it has made a connection, right-click on the NM icon, and select 'Connection Information', and it will give you information about the wireless connection: interface identifier (probably wlan0), Mac address, driver, connection speed and the various addresses. If that window shows a connection, but you can't browse with Firefox, then we need to look further.

Post a screenshot of the connection information window, and also open a terminal and post the terminal output of:

```
iwconfig
```

---

### Post by oldefoxx on 2009-12-16
I haven't been fully forthright in all this.  I don't have a wireless network here, and my interest has been mostly sparked by the fact that I decided a notebook had something to offer me when away from home, which I expect will be part of my future,  This fall we had 14 members of my wife's family gather together for a week at the beach, two bringing notebooks, and I was intrigued with how easy it was for one of them to get onto the internet through a nearby wireless access point.   That was with Windows, but I felt it was worth following up with Ubuntu, since I am getting away from Windows myself.

Now if I just upped and went somewhere with the notebook, there is little chance I could get onto the internet on my own.  Better to start now and take advantage of the wired connectivity here at home to foster and support my efforts.  And my big concern it to be able to hop onto public or unsecure access points and thereby stay current with email and such.

My wife enjoys having some of her family members and friends come over from time to time to work on sewing and embroidery projects, and a couple of them bring their notebooks as well,  I can restring my wired network to give them access, but I have considered just adding a wireless router to my network so that they could use it instead.  Pricing such routers shows this not to be terribly expensive to do.  But again, it shows a need to gain some insight into the whole area of going wireless.

My own efforts before bedtime was to try and create some new network connections, and I was already partly familiar with eth0 for the wired side and wlan0 for the wireless side.  Using the various Network Manager options, I was able to reach a point of finding two wired connections already in play, one being eth0 and the other vboxnet0. but nothing in the wireless category.  The vboxnet0 obviously related to VirtualBox, which I have on my machine, and apparently relates to the client's access to the network and ability to access shared folders.

Setting up a new network connection was a bit involved, and there is informatiom requested that is not apparent, such as what SSID and BSSID are and what they should be set to, or what the MAC address is, or the IPV4.  And if you are dealing with security as well, what type of encryption is involved and what the password for using that encryption is.  If this is your network, then you probably decided on some of these matters yourself, so just consult your notes or memory,  If it is someone else's network, then you might need to talk to them about it.

The one question I know you can answer on your own is the matter of the MAC address, this being the unique identifier that is assigned to each and every networking device during its creation.  This is rather like the idea that each and every one of us has unique fingerprints, retna patterns, or some other distinguishing aspect that marks us as separate from the rest.  So what is the MAC address?

Easy enough to find out.  There are a number of ways to find this information, but here is a simple one.  In a terminal window, type lshw and see what happens.  In case you aren't familiar with Unix/Linux jargon and desire to reduce typing, this stands for LiSt HardWare, and that is what it does.  Look for the one that claims to be the Wireless Interface, and there are the particulars for it.

  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:25:6e:da:17:7f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:2 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: bf:61:20:4c:43:9a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  
The above is what I highlighted and used shift+ctrl+C to get into the clipboard and paste here.  The description identifies it, the logical name (wlan0) is how we refer to it when creating a new network connection, and the serial is our MAC address (here it refers to the fact that new numbers are assigned serially during the manufacturing  process).

Note that lshw basically exposes everything internal to your PC, so can be a handy tool later on.  Oh, incidently, I modified the serial numbers before posting, because it does no good and might lead to some other issues to post the real ones in a public place like this.  Sort of like revealling my personal identity number, only at the computer level.

Interesting.  I've gotten this far, and have found out two things;  The first is that if I try to Add or Edit a wireless connection through the Network Manager, my accept button is not really visible.  If I move the mouse over the button's position, I am told I have to authenticate the changes, but no authentication process appears.  Something missing here, maybe?

The other thing is that it now appears that my PC is now trying to make connection with some nearby network, and I get a box up telling me that a network called "nuggles1" which uses personal encryption wants a password from me.  So it tends to suggest that I am getting in the ballpark finally.  Oh, as to the SSID and BSSID fields, online research suggests that leaving the SSID blank means that it will attempt to contact whatever access point is detected, otherwise put in the name of the access point sought.  For BSSID, you can use the MAC address of whatever whatever networked device you want to contact, so these two fields can be left blank if you are not choosy.

You know, it seems that with the information that exists in the PC, this whole process could have been made simplier.  We can see three ways that a wireless adapter can be directly coupled to the PC.  The first is by integration into the motherboard.  The second is through the use of the PCI bus.  The third is via USB. I guess we should also count Firewire.  We see that we have access to that information through tools like lshw, lspci, and lsusb.  Now how hard would it be to have a basic wireless connection for three spots automatically set up for us?
Let's say one spot is Home, another is Work, and a third is Roam.  Any spot can be flagged as wired or wireless, or even either.  For Home and Work, there are specifics to the network that could be used for a correct connection and for security.  For Roam, you just take what you can find where ever you go.

But I don't want to count this as solved yet.  Too many uncertainties remain that have to be considered first.  So ask your own questions or make your own observations, and let's see how it goes from here.

---

### Post by coffeecat on 2009-12-16
I'm not quite sure what your question is - if any - but using wireless is a lot easier than you seem to be making out. "nuggles1" is the SSID of your neighbour's network. They've set it up with encryption (probably WPA) so that you need a password to connect to it.

But it sounds as though you've sussed all this out. Good luck if you get a wireless router. Once you've configured it once it'll make more sense. As far as user-friendly configuration interfaces on routers go, I've heard that Netgear are the best, although I've no personal experience of them. From my own experience I can tell you that Linksys and Belkin user interfaces are OK, but the D-Link one I used when I first set up wireless in my home..... Oh dear, oh dear, oh dear! :( ](*,)

---

### Post by oldefoxx on 2009-12-16
Well, itwasn't 100% new to me.  I had a week's course on managing networks networks with bridges and routers about 15 years ago, and bits and pieces of what I learned have trickled back to mind to help a bit.

Two things noted.  The Network Manager wants authentication, but there is no apparent way to do this.  That is a shortcoming to me.  Second thing is that there have been many reported problems making use of the Realtek supplied components, involving video, audio, and now networking.  This is all related to using Linux of course.  There are fixes if you look for them, but search terms become critical as to what the search engine turns up.  I just keep trying, and bookmark the most promising ones, then go back and try each one on for size.

It's said that the Toshiba Satellite L355-S7915 is a poor choice for Linux or Ubuntu.  Not quite true.  I got both Ubuntu 9.04 and 9.10 on here with no problems.  Things like getting video resolution to hold from on boot to the next can be resolved, possibly by making small additions to /boot/grub/menu.lst.  Wired was easy, but it]s been a bit more involved doing the wireless bit.  I seem to be close, however.

---

### Post by coffeecat on 2009-12-16
> **oldefoxx said:**
> The Network Manager wants authentication, but there is no apparent way to do this.

Eh? :confused: You click on your preferred network, and NM pops up a dialogue window telling you the encryption type and asking you to enter the passkey. That's how it's always worked for me.

Here's a screenshot below of what happens when you click on a WEP-protected network for example.

---

### Post by oldefoxx on 2009-12-17
I looked at your thumbnail, but that is not what I get.  In my case, you try to create or edit an internet connection with NM, and you cannot complete the action because the Allow button is greyed out.  You position the mouse pointer over the button's spot, and you are then advised that your action has to be authenticated, but there is no box with your password requested.  So you have to Cancel or close the Edit Dialogue.  That is what I was reporting.  What I see that is similar to your thumbnail is when an apparent network response requires a password or key for me to get entry to a secure network. So these are two different things.

Tried to see if the network manager would still work tonight looking for hidden networks, but nothing showed up.  My nephew lives on the other side of the street a few houses north, and is into computers to some extent, but mostly as a gamer.  I asked him if he knew of a muggles1 network in the area, and he said he had seen it when looking for such, but had no idea who actually had it.  Just thought it was worth asking him.  Trouble is, get him involved in a topic like this, and you can't be sure how much being related to you is factual and what he just wants you to believe he's done or can do.

Still looking for more definitive answers, if I can get them.  As for iwconfig, here is what it shows me:

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

pan0      no wireless extensions.

---

### Post by oldefoxx on 2009-12-17
I've been working under Ubuntu 9.04 with this issue until now, but the discrepancy in what I reported and what you thought I should have made me wonder if you were under the same Ubuntu release or not.  So I switched to 9.10 today, and it is a bit different in this regard.  Unfortunately, the 9.10 version of Network Manager seems to have lost ground, because I was able to do less with it, and I could not get to a point where i could do anything with it really, but I think if I had a wireless network here at home, I might have got on it fairly easily.

Thing is, though, is that I ran into a similar stumbling block when it came to setting up connections.  The button was greyed out, and I thought it said Accept under 9.04.  I could see it at first under 9.10, and actually it says Apply.  But I tried a few changes, and it went to the greyed out state again, wanting that authorization from somewhere or somehow, but it was not apparent from where.  My guess is that the NM should only be used by root or superuser, but that conflicts with the fact that neither root nor the superuser has access to the GUI interface.  Not at all able to resolve that one, unless there is a way to manage the network from the command line in a terminal mode.

Oh, something else about 9.04 verses 9.10.  The icon for the network manager was more visible in 9.04, and it was only because of the 9.04 experience that I could barely make out where it was under 9.10.  I don't know what that is all about, because it should have been obvious to anyone looking for it that it's gone suddenly invisible, or nearly.

Is there another way to attempt wireless networking under Ubuntu?  That would be easier and potentially more rewarding than taking another Linux distro and starting over again, just to see how it behaves when it comes to networking.

Of course if you have worked with something else and it does a better job, that would be worth sharing.

---

### Post by coffeecat on 2009-12-17
Sorry I didn't reply before - I saw your earlier post but I've been out today trying not to get stuck in the snow. :(

OK. I'm still not clear if you can see any networks when you simply left-click on the NM icon. The dialogue box I posted a screenshot of is what you get when you click on a visible network. If you can see a network listed, you don't have to use the 'Create New wireless Network' choice. Until your post, I didn't realise that was what you were using - in fact I'd never noticed the thing there. Which is why, until now, I'd never tried it - I've never needed to. But I have tried it now (in Karmic) and I get a greyed-out button too whatever I do. But in my case the greyed-out button is 'create', not 'accept' or 'apply'. :?

Well - that bit seems to be worse than useless, but that's theoretical. If you can't see a network listed, then there must be a driver problem - not a problem in NM.

Let me re-iterate what works for me. If the network is not hidden, I click on it, put in my passkey and Robert is my Uncle. If it's hidden, I choose 'Connect to Hidden wireless network', put in my details, and it connects. I've just had a look at it now and if I type in some details, the 'Connect' button is **not** greyed out.

Also - if I right-click on NM and choose 'Edit Connections' and then click on the Wireless tab, I can edit any connections I have there. You have to highlight the one you want to edit before you can edit it, so I'm not clear why things are greyed out for you.

Your iwconfig showed no signal level for wlan0, so I'm more convinced this is a driver issue. I really don't think NM is at fault here.

But I agree with you about the appearance of NM in Karmic. It's a disaster imho but again that's not NM's fault. That's a theme issue. They've gone for some sort of minimalist design for all the applets around NM in the default Human theme for Karmic. Personally, I think it looks as though it belongs in Windows 95 so I've installed different themes and NM is looking healthy again.

---

### Post by oldefoxx on 2009-12-18
All sorts of cross threading issues at times  I have a Ubuntu article that tells you the steps to take to use Network Manager to get the job done, but nothing corresponds to what either 9.04 or 9.10 are showing me.  In one case I am told to go to the Network Manager this way:  System > Administration > Network Manager, but what I find instead is Network Tools.  I guess this article dates to an even earlier version of Ubuntu.  Network Tools might be useful, but only in terms of dealing with established connections, not in creating those connections.

Here are some of the fundamental things I would like to be able to determine with my notebook at the time of setting up a wireless connection:

Is there one (or more) accessable Access Points within range of my Notebook?  What strength signal is there?  Are any of these Access Points open for public use?  What name does the Access Point go by?  What is the associated IP address?  What manner of encryption is employed if not Public?  What protocol is the Access Point likely using?  802.11a, b, g, or n?  What throughput speed seems likely under the best of conditions?  What throughput speed am I actually getting?  Are there any other parties also accessing this Access Point as I make use of it?

You might think that as a user, I don't need to know all that.  I've been on the maintenance and support side of the business for a long time, and you would be surprised at what types of information can be handy to have at times.  And there have been many clues that information of that type is out there, but it is mostly associated with Hackers.  Hey, the argument that outlawing guns gets rid of crime has never been proven, and won't be as long as there are those that live outside the law or in defiance of the law.  Information can have a purpose, and it does not in and of itself entail illegal activities, but can simply be a matter of evading illegal activities by others.  Now suppose someone asks for assistance with their network, but lacks even basic information as to how the network is configured, so has little to offer to guide me.  That is a case where extra knowledge and information can become real important.

I began a new inquiry using Google and this search term:  Wireless networking linux OR ubuntu.  And as usual, a bunch of links have been listed.  I've already bookmarked a couple of promising ones.  And it's looking quite promising, even featuring some Terminal approaches that might prove good extensions to whatever overlayer that Ubuntu is willing to offer me with its restrictive approach to Network Manager.  Just thought I might pass that along in case it helps.

---

### Post by GodLikeCreature on 2009-12-18
> **oldefoxx said:**
> Here are some of the fundamental things I would like to be able to determine with my notebook at the time of setting up a wireless connection:

Is there one (or more) accessable Access Points within range of my Notebook?  What strength signal is there?  Are any of these Access Points open for public use?  What name does the Access Point go by?  What is the associated IP address?  What manner of encryption is employed if not Public?  What protocol is the Access Point likely using?  802.11a, b, g, or n?  What throughput speed seems likely under the best of conditions?  What throughput speed am I actually getting?  Are there any other parties also accessing this Access Point as I make use of it?

You might think that as a user, I don't need to know all that.  I've been on the maintenance and support side of the business for a long time, and you would be surprised at what types of information can be handy to have at times.  And there have been many clues that information of that type is out there, but it is mostly associated with Hackers.  Hey, the argument that outlawing guns gets rid of crime has never been proven, and won't be as long as there are those that live outside the law or in defiance of the law.  Information can have a purpose, and it does not in and of itself entail illegal activities, but can simply be a matter of evading illegal activities by others.  Now suppose someone asks for assistance with their network, but lacks even basic information as to how the network is configured, so has little to offer to guide me.  That is a case where extra knowledge and information can become real important.

I began a new inquiry using Google and this search term:  Wireless networking linux OR ubuntu.  And as usual, a bunch of links have been listed.  I've already bookmarked a couple of promising ones.  And it's looking quite promising, even featuring some Terminal approaches that might prove good extensions to whatever overlayer that Ubuntu is willing to offer me with its restrictive approach to Network Manager.  Just thought I might pass that along in case it helps.

I really think you are making a very simple thing way complicated.

Like coffeecat already mentioned, you just need to left-click on your network manager applet icon under the system tray.  I have been using Ubuntu for a while and all versions from 8.04 to 9.10 show the same behavior (almost 100% similar in this regard).  

As I was saying, simply left click on the network manager applet and you will see a list of the available wireless networks within range.  Each network should display a name, and you will see a little icon to the right of the name which displays the signal strength your computer is detecting.

If you left click on any of those networks, assuming they are encrypted, you will get a prompt asking for the pass key.  At that point you will be able to tell if they are WEP or WPA encrypted.

Now, in terms of "protocol", as you put it, it is a bit less important, if you ask me.  Most access points and wireless cards support b/g/n at the moment, so you should be OK.  These specifications are clearly explained on the actual access point packaging and instructions, though.

In terms of throughput, once again, not easy to tell right off the bat.  If you run ifconfig and iwconfig commands from a terminal, you will get some indications.  There are also internet sites that measure the speed of your connection.  You should compare the actual speed your machine is reporting through such sites and the speed your provider is supposed to be servicing you with.  That´s probably where the biggest gap may be.

As for finding out if someone is using your network, well, again, not an easy task, and a big time waster in my opinion.  If you take the necessary precautions, you should be OK.

Basically, you should do the following:

1.- Set up your network as hidden.  This would avoid that your network becomes an obvious target.
2.- Disable DHCP and use fixed IP addresses.
3.- Use WPA2 encryption.
4.- Some routers/access points display when clients are connected using wireless connection.  Once you shut down your PCs, it is a good check to see if connections are still displayed.  Note that Microsoft clients do not close their connections immediately as they should, so you may still see the connected light on for a while.
5.- Do not leave your router on at all times.  Shut it down when you don´t use it.  Not only this is good from an energy saving stand point, but also you would dramatically limit the amount of time anybody could attack/try to hack your router.
6.- Change your encryption key on a monthly basis.

I can assure you that it would be almost impossible for anybody to hack your network if you follow all of these suggestions.  However, some of them may be complex for a standard user, so just stick to items 3, 5 and 6 and you´ll be fine.

Good luck

---

### Post by coffeecat on 2009-12-18
> **oldefoxx said:**
> Here are some of the fundamental things I would like to be able to determine with my notebook at the time of setting up a wireless connection:

Is there one (or more) accessable Access Points within range of my Notebook?  What strength signal is there?  Are any of these Access Points open for public use?  What name does the Access Point go by?  What is the associated IP address?  What manner of encryption is employed if not Public?  What protocol is the Access Point likely using?  802.11a, b, g, or n?  What throughput speed seems likely under the best of conditions?  What throughput speed am I actually getting?  Are there any other parties also accessing this Access Point as I make use of it?

Just to pick up a few of those points: why would you want to know any of this except for your own network, a neighbour's network where you have permission to connect, or a publicly open access point? I don't know about the law in your country, but here in the UK connecting to a wireless network without permission is a criminal offence. A story, I believe true: Two police officers were doing their rounds in the streets of Chiswick where they came upon a young man sitting on a front garden wall (not his own) happily surfing away on his laptop - in broad daylight. Upon being asked to explain himself the, clearly naive, young man cheerfully told them that he had found an unsecured network (in the house of the garden on whose wall he was perched) and decided he would take advantage of it. At which point the two officers invited the young man to accompany them back to the police station. :rolleyes:

But to specifics:

NM will tell you how many accessible networks are in range.

How do you tell a public access point from an unsecured private one? I don't know, except public ones tend to be advertised.

The name of the access point is the SSID.

IP address? Why do you need to know this? NM will discover this when you attempt to connect.

Type of encryption? NM will tell you this when you try to connect.

Protocol: all 802.11 devices are backwardly compatible, so the speed of the connection will be determined by the slower of the devices. For example, if you connect to an N router with a G device, you'll get no faster than G speeds.

Throughput speed will be maximal in the best of conditions, but the best of conditions are rarely met. NM will tell you your connection speed.

Why would you want to know if other parties are accessing a public access point? If you mean your own router, you can log in to your router configuration interface and that will tell you what devices/computers are connected.

> **GodLikeCreature said:**
> 
1.- Set up your network as hidden.  This would avoid that your network becomes an obvious target.
2.- Disable DHCP and use fixed IP addresses.
3.- Use WPA2 encryption.
4.- Some routers/access points display when clients are connected using wireless connection.  Once you shut down your PCs, it is a good check to see if connections are still displayed.  Note that Microsoft clients do not close their connections immediately as they should, so you may still see the connected light on for a while.
5.- Do not leave your router on at all times.  Shut it down when you don´t use it.  Not only this is good from an energy saving stand point, but also you would dramatically limit the amount of time anybody could attack/try to hack your router.
6.- Change your encryption key on a monthly basis.


Just to add/comment on what GodLikeCreature posted:

Personally I don't bother with hiding my SSID, but do change the SSID from the default.

That's an interesting point about fixed IP addresses.

Yes, do use WPA, preferably WPA2. **Don't** use WEP. And when you choose your passphrase, use a mix of lower-case, upper-case, numericals and special characters. Avoid dictionary words.

**Always** change the admin login username and password of your router interface. Sometimes you can only change the password. Remember that screenshot of the NM passkey dialogue I posted? That was from a neighbour's network, and they have made several fundamental mistakes. They did not change the SSID from the default of 'NETGEAR'. They are using WEP which could be cracked by a competent cracker in minutes. And I'd be prepared to bet serious money that the admin name and password are still 'admin' and 'admin' (or whatever Netgear uses). Which means that a competent cracker could crack the WEP key, login and reconfigure the connection for their own use or just to do mischief.

Last thing. Don't bother with MAC address filtering. Any competent cracker can sniff out and emulate MAC addresses with ease. It'll only give you a false sense of security.

---

### Post by oldefoxx on 2009-12-18
All good points, as I've read them cited elsewhere.  But it is good to have them together here for others to become aware of.  Let me make the added point that if you limit yourself to a wired network at home, you are a lot less exposed to bypass hacking and will get better throughput as well.  But a lot of people are really taken with the idea of being wire free, just as they are with cell phones and iPods, so the desire to go wireless is almost engrained at this point.

But if you are aware of and concerned with the possibility of identity theft, which is rated the fastest growing crime in this country, then you really ought to recognize that you really expose yourself if you go wireless without adequate safeguards in place, and you are the architech and enforcer of those safeguards.  They don't just happen by themselves.

You might know that your home phone cannot be tapped by the government legally by anybody, including the government, without a court order. 

But any judge can sign a court order, and illegal wiretapping does exist, even by the government.  The real concern about the legality issues only become apparent if facts taken by this means are to be the basis of further legal actions involving the court system.

But it is unnecessary to get a court order in cases involving wireless transmissions, because that is making use of the airways, and presumably you cannot assume privacy in what you say or what is said to you if it gets on the air, meaning carried  by radio waves, even for just a short distance.  Taken further, you might be safe from a wiretap  at your end of a conversation, but what of the other end, if taken over a cell phone?  

Now we are talking about computers, networking, the internet (which is known not to be safe in many respects), and the actions of others if you are so careless as to let them do what they want when you do not take adequate steps to protect yourself.

It's also true that using another's internet connection without their knowledge or permission is illegal here, but how do you know?  If you cannot distinguish public from private networks, nor have a way to see if someone else is making use of it, nor a means of identifying that person at the time of the event, then who is to make the distinction and how?

Those two officers of the law were lucky to walk into a scene where the activity was apparent, and the person acting in that fashion elaborated enough so the extent of the crime could be determined.  Had he a cover story handy, or switched to a game of solitaire before they got too close, all they really could have done is advise him to get off the wall as it would serve as a private property boundary.

And while it might be true that the law is against using unauthorized network access, that does not prevent some people from driving or walking around monitoring for hotspots, even marking walkways and walls where they are found for others to use.  After all, one could argue that only public networks should be apparent, and those that want to restrict access should all be hidden, because to be visible is to invite participation (implying that they signalled you first as an invite).  

Why make a point of all this?  Because it serves to answer the argument that I am making it needlessly complicated.  The whole trick to successful wireless networking is to ensure that it is complicated enough to defy those that would transgress and penetrate it, and why you need to ensure that level of protection.

Think of it this way.  Given all the time in the world and with endless resources at hand, there is no doubt that any bank vault can be penetrated,  Vault security is designed to hide the mechanics of how to get in (like behind a combination wheel), demand too much in terms of resources (the more equipment brought in, the more expertise required, the longer it will likely take), and to limit the time in which the thieves are free to work before being detected (security cameras, sound monitors, temperature sensors, security patrols, all serve to cut up long chunks of time by reporting anything unexpected).  But many major banks have been plundered over extended weekends or under other circumstances not allowed for, such as by tunneling from other structures.

Look, in one respect, the mighty Egyption pyhramids were some of the greatest vaults ever built by man, especially for the age in which they were conceived and built.  But each was eventually plundered by those that were committed to that enterprise.  All they needed was unlimited time and the tools at hand.  Eventually, the idea of preserving the tombs became both a matter of a distant location and hiding all evidence of the tombs' presence.  Some did survive in this fashion,  

The idea of protecting data and information has become more a matter of the form it takes, such as using encryption, and less concern about if or how someone acquires it in that packaged form.  But given time and unlimited computational power, and the fact that encryption always has its own rules that it follows, it is just a question of how long it will take before the form surrenders and gives up the data and information contained inside.

This might be far too long do for the encryption method to be of serious concern, at least at present, but as computers become ever more powerful and numerous, the actual time for decrypting stored forms is likely to get shorter and shorter.

And once a form is in the wild, say put on the internet, there is no way to get it back or ensure that copies are fully eradicated from every eventual resting place.  What you can hope for then is that there will be so much encrypted files on hand that it might take thousands of years until they work around to any that might prove really damaging once the contents are revealled.  There is also the fact that sometimes information is only relevant in a given context, and that it will be virtually meaningless once it sees the light of day again.

How might this apply?  Remember some years back, before they found the resting spot for the Titanic, that a film came out in which is was located, and intact enough that they showed the whole rusted hulk being raised back to the ocean's surface?  If you saw that, you should not have forgotten the fine show they made of the whole thing.

But later the Titanic was found, and on finding and exploring it, they found that it's back had broken and it had come down in two sections, the bow and stern were quite far from each other having sunk separately,

Now if you were to see the film mentioned after that disclosure, you would realize the impossibility of the Titanic ever coming back up to the ocean's surface in one piece.  in this case, the only real knowledge or data was the assumption that it had sunk in one piece, and that lent creditability to the idea of raising it again.   But in the light of later real information, the basis for the whole movie was utterly eradicated,  This is what I mean by information in context, which can sometimes relate to noninformation or misinformation as well.

Interesting topic, but I guess not for those in a rush to be somewhere else or doing something important.  Still, all this has some bearing on my interest in the matter of linking my notebook to the internet or elsewhere, and to how to go about it.  If you are happy with the little that NM tosses your way, then that is fine by me,  I'd rather go a bit further myself, if you don't mind.  And I am sure you don't, as long as it is not taking up your time and space.  That's a fine fellow.  Bye.

---

### Post by oldefoxx on 2009-12-18
Man, you want some real reading, pick one of these links:

[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/)

[http://www.brighthub.com/computing/linux/articles/46111.aspx](http://www.brighthub.com/computing/linux/articles/46111.aspx)

[http://wiki.eeeuser.com/guidebooks:basic_linux_commands](http://wiki.eeeuser.com/guidebooks:basic_linux_commands)

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

Just the first one is going to keep me busy for days.  It's one you can't read just once and get the full measure of, and it relates a lot of history behind Wireless Development that is not apparent on the surface.  But there might be something there in all this to appease me, and I might learn of some ExpressCard 34 or 54 approach that migh fill the need as well, especially if at the newest 802.11n level.  I mean you have so much going on at once, from kernal improvements to new driver efforts and even firmware and hardware upgrades along with new developments. and that is all going to add up to something different sooner or later.  
.

---

### Post by Extract_Here on 2009-12-19
I hate this problem the same thing happened to me when i first installed 9.04. Your going to need to achieve a direct connect from the router so you can get the correct software to install your wireless driver. 
 The things you will need to download 
1. ndiswrapper you can get this from the synaptic package manager 
(system>administrator>synaptic) 
2. You will need to find the driver for your wireless card(google search its brand name along with driver. eg. ("Belkin" Driver) download it even if its a Windows Exe. file 
3. Browse the windows exe. file and find the file with .inf on the end eg. (belkin.inf)
4. once you have found that file open up Ndiswrapper It has a different name in the menu its called windows wireless drivers. (system>admin>windows wireless drivers)
5. drag the .inf file into the NDiswrapper and your wireless should connect.

if your still having problems message me and we can talk further.

-may the source be with you

---

### Post by oldefoxx on 2009-12-19
That is an excellent point about using ndiswrapper.  This is a unique concept in the PC arena, that all peripheral devices of a given type could be supported in another OS via something called a wrapper.  In a sense, a driver is a kind of wrapper, but now we are talking about a wrapper for a driver as well.  It's the standards set forth for networking that has made this possible.

There are not similar standards for other devices that will allow them to function under other operating systems as though under the original one, so when it comes to things like printers and scanners, you are in deep trouble, unless by chance they will run under Wine or one of the VMs,  Well, there are a few excepxtions, such as USB and various drives.  If a standard format is employed, such as FAT32, NTFS, EXT2, EXT3, EXT4, and so on, someone may have actually written a driver that can read, write, format, and even check the drive for problems.  For instance, you want to access your Windows NTFS partitions under any version of Linux, just download and use the ntfs-3g drivers that let you do this and make the necessary association either in /etc/fstab or with -t (for Type) in the mount command.

I did mention that 9.04 does have what appears to be an experimental driver for the RTL8187B USB-to-wireless controller, and it does appear to work, at least partways, in my limited circumstances.  So now you see you have two ways of trying to go at this:  With what is there, and with what can be added using the ndiswrapper method.  For me, the driver version under 9.04 is slightly more interesting in terms of results than I got with a somewhat different driver version under 9.10.

Would a serious Linux buff use ndiswrapper?  I guess that depends.  In my readings yesterday about the Wireless development effort for Linux, I found where one developer had used ndiswrapper to load and use a USB to Wireless card that was not subject to disclosure by the manufacturer.  He used the Wireless card in various ways, and monitored the generated traffic on the USB side, and was able to document a correlation between the two that served to help write a separate driver that was specific to Linux.  Apparently he thought it was good enough for that purpose at least.

But if ndiswrapper is good enough for that purpose, why not just use it and let matters go?  Well, first ndiswrapper only works for networking, and what it does cannot be applied to everything else, in fact it applied to nothing else.  Second, Linux is a legitimate operating system choice, and many people feel that manufacturers should respect it as such.  After all, they sell equipment, and it should not matter if the computer involved is running under Windows or some flavor of Linux.  It should be owner's or user's choice in the matter, and for manufacturers to hold out and only supply Windows' drivers with their equipment is pushing the controlling monopoly where Windows is concerned.  Some even wonder if there is not some financial consideration given to certain manufacturers to encourage this attitude.

There are certain standards in other equipment categories, such as PostScript when dealing with certain printers, or TWAIN when dealing with some scanners.  These might serve as sort of a foundation for creating compatable drivers, but actually there is a lot of hardwaring involved here that is not covered by these, such as monitoring ink levels and paper feed and jams, performing jet cleaning, checking for document boundaries, and using user input as part of any job.  These devices therefore require additional program support in addition to the use of hardware specific drivers, and usually take special install methods to get everything in place and working together properly,  And while drivers might be okay in and of themselves, those added programs are going to be operating system specific in nature, not able to run by themselves under an alternate OS, or even be installed under that other operating system. 

The general plan then is, if going to or sticking with Linux, such as with Ubuntu, take actual hardware involved into consideration.  If you need a printer or scanner, check out whether the model you are contemplating can work with that Operating System or not.  It's not a case of try before you buy, but of check online and save some time.

---

### Post by yelvington on 2009-12-19
*Is there one (or more) accessable Access Points within range of my Notebook?  What strength signal is there?  Are any of these Access Points open for public use?  What name does the Access Point go by?  What is the associated IP address?  What manner of encryption is employed if not Public?  What protocol is the Access Point likely using?  802.11a, b, g, or n?  What throughput speed seems likely under the best of conditions?  What throughput speed am I actually getting?  Are there any other parties also accessing this Access Point as I make use of it*?

The taskbar NetworkManager applet lists all visible access points, ranked by signal strength. The name is visibly displayed. The signal strength is shown on a four-bar scale. 

If a large number of APs are available, additional APs are listed in a fold-out. 

If an AP is secure (requires authentication), a lock icon appears next to the name. Unless it's your AP, you can safely assume that you are NOT welcome to use it.

IP addresses are not displayed because there is NO IP ADDRESS associated with an access point until AFTER you have connected, authenticated, asked nicely for an IP address (presumably using DHCP) and been granted one. At that point you can right-click and select "Connection information." You'll also see the name of the driver in use, and the current connection speed.

There are various "wardriving" scanners for Linux, Windows and OSX that probe for some of the other information you are interested in, but I don't know of any that actually works with Ubuntu and any network cards that I own. I know of NO software that tells you who else is connected to an AP, which would be quite a privacy violation.

As far as I know, the authentication protocol is not revealed until after you connect and ask to be authenticated.

If you're in a populated area and you see no APs showing up in NetworkManager, then you may have a driver issue. If you do see APs showing up, find one that's open and attempt to connect while running the following command in a terminal:

tail -f /var/log/syslog

All the various Linux networking tools eventually talk to lower layers that log what they're doing.

I don't think you're going to get very far testing your system unless you have an access point, so I'd suggest you head to a public library, coffee shop, etc., that offers Internet access and do your testing there.

---

### Post by oldefoxx on 2009-12-20
It's really good reading the responses that have been comming for from others, and while I did apparently detect one network near here apparently with the SSID of "muggles1", it is secure and no others show up at all.  It's an older established neighborhood, and I would suspect that that there are few access points around.  However, I do know of two others, a Linksys setup my brother-in-law has just two houses over, and whatever setup my nephew has diagonally across the street, but he and I rarely talk.  Now when running 9.10, I haven't even seen "muggles1" yet.

So I have to take your word for it that either I have driver issues, or that there is just nothing in range to be seen.  Not being instructed any better yet, I did get another tool downloaded and installed,  named RutiIT WLAN Manager and played with it briefly.  It seems to do no better, but does give me some possible leads based on returned errors, such as the only working mode offered is Managed, the only security choice offered is WEP, and you can try to manage a connection on any one of 14 channels.  I actually played with both methods to see how they interact, and I think I fooled the system into thinking I had a working network connection, but one with no traffic, no signal strength, nothing to mark it a usable.  Oops!  Repeating my steps to verify how I did this, it just happened again.  Now I have two standing antenna rods and four bars indicated side by side on the toolbar.  Nothing really there, though.

According to what I've read to date, if you name a SSID as part of a connection, that is the only access point that will be sought.  If you leave it blank (I one case I saw internally a "" was used to show no specified SSID), that should be good for any open network including public ones.  But when I try to use RutuIT, it demands that an SSID be entered manually.  Another case was found where you either had to specify a SSID or an IP Address.  Hey, if you don't have any working connections to relate to, that is not information you have in hand.  If you are creating your own access point, then you can decide what to put in.   Now with Cox.com, you pay extra for static IP addresses, and the normal thing is just to work with dynamic ones.  If crouched behind a router, you will likely use the local IP addresses that it comes with it.  But not having set up an access point myself, I have no idea what Cox might have allocated, so again, I'm apparently overreaching what is accessible to me at this point.

Interesting thing about wireless adapters and drivers is that it can be difficult to determine beforhand what might be possible with a given setup and what is presently out of reach.  For instance, there are different levels of encryption, and sometimes only WEP is available,  Scanning may or may not be possible, but where it might be possible you are dependent on the Wireless Extensions (I haven't gotten into what those are yet, something more to learn).

So anyway, these are all elements that I have been running into in the Wireless arena, and when I wrote out what I was looking to be able to do, I had yet to run into the fact that most adapters and drivers only give you a portion of the whole.  You are not going to get an all in one, and that is what some of you have probably realized and were trying to convey to me as this thread has gone on.

Well now tell me, aren't there a range of devices that are available that help in this regard?  I mean, some sort of handheld instrument that reports on detected access points and signal strength?  One of you wrote and said that I should already be getting this through the Network Manager for any detected networks near here, but as I stated, I seem to see one called Muggles1, but nothing beyond a request for a password in order to access it.  I know my nephew has wireless, and with his discretionary income and wanting always to have the best of it, I would be willing to bet that he is using 802.11n, and I think that means we should be within signal strength of each other.  I'm nof trying to get a free ride off anyone, I just want to be able to see what is there, or at least as much as can be seen.  And if what I have is not adequate for the purpose, then I want to know that as well.  But it is proving to be a bit hard to find out for sure.

---

### Post by oldefoxx on 2009-12-31
I keep diddling in this area from time to time, but nothing significant to report as of yet.  I used apt-get install network* to see what all it would grab,  which was a ton of stuff, but then tinkering with some of the results were not very helpful.  I thought of using apt-get install wireless* to see what else might get added, but decided the overload was not that promising.  I also used the Package Manager to see if I could find a match for RTL8187B with Ubuntu 9.04, but the only close match was to RTL8187SE, and these are not the same.  Just makes me wonder what wireless adapter was actually involved in cases where it is suppose to work right out of the box.

I've also asked myself is there might be some way to make the notebook only function as a signal monitor for the immediate area.  What I learned all those years ago is that you can use an interface card either to just monitor a connection, or to engage and act with the connection, but not both.  We did not get into why this is so.

Anyway, not being a party to any of the local networks, I just thought it ought to be possible to study the area for signals, maybe in terms of direction, frequencies used, and strength.  The idea being that this might be useful when traveling or trying to judge the reception distance from the access point to a given distant device or position.

I could not find anything really instructive on doing this, but some of  the packages loaded might play a role in this area.  However, I decided that I had exposed myself to way too many packages without knowing what they did or how to use them, and decided to reinstall Ubuntu 9.04 and go back to scratch and work forward from there.

A number of efforts to make directional antennas for wireless have been reported, and the claimed distance increase in one direction has been notable.  A common design involves a parabolic shape and central rod, not too hard to make on one's own.  There are also a number of onmi-directional antennas being sold for the same purpose.  But do you need one, and what is the best place and direction to point it?  I also read that you can get a meter that helps determine these things, but why buy a meter if you can do it with software and the equipment you have?  That's my point.

---

### Post by oldefoxx on 2010-01-03
A couple of days left before the packaqe with an ExpressCard and an Access Point should arrive for me to carry forth with.  During the holidays I did learn two things.  An upteenth reinstall of Ubuntu 9.04 finally allowed me to recognize four nearby metworks, and I had no problem accessing the internet through my wife's best friend's network, which is unsecure.  That proves that the adapter is working, and maybe suggests that the install process is a bit sensitive when it comes to detecting the adapter, often failing in the attempt.  That was with Ubuntu 9.04.  I've already reported another problem with 9.04, that it somehow loses access to the high resolution settings offered by my video card, and that requires a reinstall each time to try and surmount the problem. 

I am just using Ubuntu 9.10 right now, as the low resolution issue with 9.04 was getting in the way of too much, but I have yet to see an instance where I can get anything out of the network adapter under 9.10.  About two more days for my wireless shipment to arrive, and maybe that will help me get someplace.

---

### Post by oldefoxx on 2010-01-03
I was taking steps with my VirtualBox clients to share all my emails received and address book among them (there being two effective ways to doing this with ImcrediMail), and needed to get a client to recognize and work with a USB connected hard drive, and suddenly realized that my RTL8187B Adapter was available to the client, so I enabled it.  The client, Windows 2000, promply identified new hardware, even what it was, and wanted a driver for it.  So I found a recent driver at Softpedia and downloaded it.   I wanted to save it to the hard drive for reuse, but now I have to wait for a drive check to complete, which will take some time.

Now wouldn't it be interesting if a Windows client is able to rely on my wireless capabilities, and able to confirm again that the adapter is working?  You may think a client is rather limited, but the fact is that with VirtualBox, the host and client are able to function at near peer to peer levels, and can have access to all devices, folders, and files through the agency of VirtualBox.  So this could get real interesting.

It really gets down to a matter of shared folders and designated USB devices that the client can have access to. These are controlled by the Settings enabled for each client under VirtualBox before starting the client.

---

### Post by oldefoxx on 2010-01-04
Okay, I am still talking in regards to the Windows client here.

I finally found and installed a RTL8187B driver, or at least it goes by the label.  Trouble is, each time I found one, either it said that the hardware did not match, or if it installed, might say it was working, but the next reboot would state otherwise.  In fact the only driver that would install at all is the one that performs an auto install, so I added "auto" to my search criteria.  I also got an error 31, which only says that something else in the PC that was needed was not working.  Isn't it wonderful how informative the Windows' Troubleshooter is?  I've yet to have one case where it actually helped when faced with a problem.

Points out that the distance between Linux and Windows is not all that great when you get beyond just the surface aspects.  I don't mean that the OSes are alike under the hood, because they are not, but in one respect they to tend to be similar, which is finding answers to problems is not all that easy.  But at least with Linux you have a vast community to turn to that can sometimes help.  Windows is much vaster, in terms of users, but these are more casual users and less inclined to try to resolve their own problems when there is a computer shop over at the mall, or a very sharp crony that they can turn to.

---

### Post by viper3ez on 2010-01-04
ok, i have a similar problem so i'll thread jack.
 
i just installed 9.10.
 
when i left click on the network icon at the top, i see wired network grayed out and saying disconnected but no wireless or list of available wireless.
 
i also see vpn with an arrow to a submenu for vpn options.
 
all the above is when i left click.
 
when i right click, i get an option to enable networking which is checked and then connection info which is grayed out and then edit connections and then about.
 
this is a dell mini 10 that originally had dells ubuntu 8.04. 
 
any help please

---

### Post by oldefoxx on 2010-01-10
Well, misery loves company.  Got my wireless-N router and ExpressCard on time, and have been going around the horn ever since.  There are so many settings to consider with the router, and I am trying to work out what is best, but so far it all seems to be a matter of choice, with no clear idea of what to choose or why.  So far the router is just plugged into my other router and wired to the notebook as I sort things out.  The Radio setting is turned off, meaning that right now I am off the air.  Haven't tried anything with the new ExpressCard yet.  I printed out the 55-page on-CD manual, and am still making my way through it.  Been back online trying to find a good How To Set Up a Wireless-N Router for Home Use.  As far as I can tell, it hasn't been written yet.

Have found some other good stuff though.  For instance, some cards and some drivers support network monitoring, meaning being able to tell what is going on with your own network and with the wireless stuff around you.  Finding out which does what is much harder though, hardly ever mentioned with specifics involved.  It's related to NIC, anyway.  That's something to know.

I also stumbled on a chart of what wireless drivers support what cards in some of the lesser languges, meaning Linux, BCD, and the Mac.  This can be real handy, and here is the link:  [http://en.wikipedia.org/wiki/Comparison_of_open_source_wireless_drivers#Driver_capabilities](http://en.wikipedia.org/wiki/Comparison_of_open_source_wireless_drivers#Driver_capabilities)

If you work down through this list, including notes at the bottom, you find three references to what works with the RTL9197B adapter.  This is the RTL8180- SourceForge effort, but redesignated the rtl-wifi at another place in the list.   Looking for rtl-wifi took me to another place, which covers steps to acquire and install the driver:  [http://rtl-wifi.sourceforge.net/wiki/Installing](http://rtl-wifi.sourceforge.net/wiki/Installing).

But now remember, this driver is already suppose to be pre-installed in the Linux Kernel since build 2.6.27, and Ubuntu 9.xx is well above that.  So what is the problem?  Can't be sure, but I note a couple of things that are out of place.  First, in the driver comparison chart, there is no specific mention of RTL8187B having a USB interface.  It could be that someone just assumed that this RTL818x was like the others, and this driver would work as well with it.  Second, there is mention of the fact that the stack normally used in the kernel for this function is not adequate, and there are instructions for changing it out.  Maybe that got crossed somewhere as well.

But I have to be mindful that I did have that one time experience where my wireless got onto my wife's friend's home setup, so my guess is that I am well enough configured, but maybe lack some of the mentioned capabilities that fall within the wireless standards.

Oh, here's the main page I finally got back to:  [http://rtl-wifi.sourceforge.net/wiki/Main_Page](http://rtl-wifi.sourceforge.net/wiki/Main_Page)

What sort of gets me right now is that when over at my wife's friend's during the holidays. I saw four networks, with hers having the strongest signal.  I don't remember how I did that.  I had something going that was able to show that to me, but what was it?  I'm not sure.  It's sort of like the people that put Ubuntu, or maybe Linux in general, just thought it was unnecessary to know any of this, so why provide decent tools to make any sense of it all?

This seems to be a good link too, for several reasons.  Make note of the links offered at the bottom, which also have things of interest to relate:
[http://www.speedguide.net/read_articles.php?id=2556](http://www.speedguide.net/read_articles.php?id=2556)

---

### Post by oldefoxx on 2010-01-10
Man, this chase is taking me all over the map!  Not so bad, because I am coming into contact with new things, but in terms of getting the job done, this is not so good.  I've been at this one problem for months now.  A few good ideas were offered near the beginning, but nothing really panned out, and when others make claim that they had no problems themselves, people probably begin to doubt you even know what you are writing about.

Know how many threads start off with a problem, go a few posts as someone asks for more information, a few suggestions made, and then it just runs out?  No idea myself, but I am finding them all over.  Was the problem fixed?  Can't say, it's not a part of the thread.  What was the real problem?  Don't know, apparently nobody really in the know bothered to respond, most likely busy elsewhere.

I'm trying to work through a process described in one article, but I cannot do it, because it seems to be specific to a Linux release called Gentoo.  There you have a command line process called "emerge" and make use of a file called /etc/conf.d/net.  Doesn't match up with Ubuntu, I am afraid.  So what should I do instead?  I guess go search for a similar process related to Ubuntu, but you know that isn't likely to be found anywhere.  Sometimes if you just knew what it was exactly that you were suppose to be getting done here, then the means of doing it might be worked out for your distribution.

Anyway, it was attempting to set up a script for iwconfig, and made an effort to explain that ifconfig was useful for networking, but that iwconfig was more specific to wireless networking.  The language for the script file showed a couple of interesting ways in which iwconfig might be used, in our case here you might start with "iwconfig wlan0", then maybe tag on a certain parameter and how you wanted it set.  It said that you probably needed to use ifconfig wlan0 up, which would turn the adapter on for further configuration.  Without the script, I tried it, and the result was not what was expected.  What I got was:  SIOCSIFFLAGS: Unknown error 132.

Don't you just love numbered error codes?  They've been around for a long time.  Used to be, when computers where much bigger, slower, and had both less memory and storage, that numbering errors meant that you did not use up too much of a limited commodity.  What you had then were long error encyclopedias organized by number, and you could look it up for yourself and find out what it meant.  Well, we got well away from the error encyclopedias in recent years,  but we are still stuck with the numbers. So what does it mean?  Do a search engine check of what's on the internet.

This is not that uncommon an error, but nobody knows exactly what it means.  What some have deduced though is that apparently the network device is not responding.  And from some genius' lead, several have decided to try a series of given commands to see if it would help.  The
reported results have been mixed.  in general, these are the steps:
rmmod ath9k
rfkill block all
rfkill unblock all
modprobe ath9k
rfkill unblock all
ifconfig wlan0 up

wifi works correctly

There are variations in different posts.  In some, instead of rmmod ath9k,
they specify modprobe -r ath9k.  But that's not for us, because the module we are concerned with is not related to aetnos chip sets, used in some other wireless adapters.  Instead, we should probably be concerned with the two modules identified previously, either rtl-wifi, or its predecessor, rtl8180.

Aside from that, rfkill might be the culprit, somehow blocking some radio frequencies when it should not be.  For reasons not given, it seems desireable to try to block them all first, then to try to unblock them, after which another modprobe will reactivate/reinitialize the wireless module.

I'm just trying to work this out in my head rather than chase down another path again at the moment.  Too bad posters can't learn to post comments along with their lines of code as programmers are encouraged to do.

Okay, but jumping back to the question of which module is involved, this suggests that if rtl-wifi is in the kernel, modprobe should indicate this.  But on Ubuntu 9.10, this fails.  I take it to mean that rtl-wifi is not included in the kernel.  Trying again with modprobe rtl8180, it looks like that one is included.  But my reading to date suggest that rtl-wifi is the newer, and presumably better version.  Still, it should work, right>

Well, there is at least one bug report open that says this might not be the case.  Here is a link to it:
[http://osdir.com/ml/debian-bugs-dist/2009-12/msg00148.html](http://osdir.com/ml/debian-bugs-dist/2009-12/msg00148.html)

Now this link gives you more specific instructions of how to manually try to work around the problem, and some explanation of what might be going on.  Someone else might want to look at the possibility of replacing rtl8180 with rtl-wifi and see what difference that might make.  Me, I am just glad to have finally made a little progress here, and hope something works.  We will see.

---

### Post by oldefoxx on 2010-01-12
> **viper3ez said:**
> ok, i have a similar problem so i'll thread jack.
 
i just installed 9.10.
 
when i left click on the network icon at the top, i see wired network grayed out and saying disconnected but no wireless or list of available wireless.
 
i also see vpn with an arrow to a submenu for vpn options.
 
all the above is when i left click.
 
when i right click, i get an option to enable networking which is checked and then connection info which is grayed out and then edit connections and then about.
 
this is a dell mini 10 that originally had dells ubuntu 8.04. 
 
any help please

I didn't take time to respond directly before.  You went directly to version 9.10, whereas I went for 8.04 to 9.04 first.  9.04 was different, but not bad.  I found moving on to 9.10 difficult, and I am talking about 3 different computers set up different ways here.  The only PC I have that worked both with 9.04 and 9.10 was the Toshiba Satellite L355-S7915, but I have had other problems with it, notably the screen settings, and most specifically the efforts to use the built-in USB Wireless-G LAN adapter which is idenfified as RTL8187B.  The one time I did get it to work, that was with 9.04 running.  When I rebooted into 9.10, it did not work.  Going back to 9.04 caused it to work again.  I was curious about which driver might be involved in both, and modprobe indicated rtl8180 in both cases, and did not indicate rtl-wifi in either case.  It also indicated rfkill was present, but the two desktops indicate that it is not.  So maybe I picked that up somehow when trying different things.

I think I stumbled over a link that was related to installing RTL8187B support specifically to 9.10, but heck, with so many links to go with, that one got away from me.  I will try to search it out again tomorrow.

Right now I am sort of interested in the idea of being able to monitor for local wireless transmissions from a live CD or DVD.  A couple of choices here, and I am downloading them both.  That way I can tuck in a disk and check for local nets when it suits me.  I also read just how fragile the WEP and even the WPA encryption processes are.  What I noted in my readings was that those wanting to break the codes can take advantage of a given, which is that the protocols and some of the messaging are almost a dead giveaway for how to attack the encryption overlay.  Here is a small example to illustrate this point.  Emails tend to have standard headers, such as:

From:
To:
Cc:
Date/Time:
Subject:
Text:

Within each field, the text normally runs left to right.  The text field is usually the most extensive, often starts with a greeting, introduces the subject to be discussed, lays out points or arguments in support of a conclusion, then end with a conclusion.  All this is a left-to-right, top to bottom sequence of words in a given written language, with certain characters used for certain things, like commas, CAPITALIZATIONS, and periods.  Oh, don't forget spaces, which are the most commonly used character of all, and serve to separate words from each other.  With identifiable word groups once you have space separation throughout, you have an edge on breaking the code within.

The real thing though could just be the protocol exchanges in negotiating communications and exchanging information.  If these are subject to encryption, then isn't it the same encryption used for the communications contents?  Almost certainly.  And aren't those protocols set forth in standards so that anyone can rather easily communicate with almost anyone else?  You just have to stick with the standards, right?  Right. And that immediately says that some of the exchanges are known for the purpose that they have to serve, and from that something is revealled about the encryption being used as well.  And it's been proven that no system is that secure that it cannot be defeated in light of the fact that someone can reach it, can study it, and find its weaknesses.  The study is simplified by the fact that computers can do the ardious work. 

What makes all this more certain is that even the government and the military rely on commercial products, and while the contents may deserve to be kept secret, the information on products and standards is all readily available. Even the manner of encryption may be known in advance,
and the math involved readily understood.  What is lacking is the encryption key, but keys too weak or left in place too long are another area of vulnerability, and the manner of generating or replacing keys is subject to risk as well.

Really a major risk problem, one reason I've shed away from wireless for so long.  But so much of your personal information is now exposed via the internet that identity protection is almost to the state of where to say that wireless just makes it worse does not mean that much increase in total risk.  Some study and knowledge of what puts us at risk may now serve to help us find ways to cordon off the areas of greatest exposure.

See, I want to do wireless, to know when and where wireless is do-able, but to understand it well enough not to make things worse on myself.  That is what I am looking for at this point.

---

### Post by oldefoxx on 2010-01-12
Hoo.  Haw.  Yeah, I write a lot.  Sort of summarizes the time and effort made to date.  To explain it to others just helps me clarify my thoughts.  I hope it is of some value.

My example of messaging using an email form was not entirely suitable, but I wanted to get down to a point where most people could make an association with the topic.  Think of it another way, human communications.  You've seen movies where two strangers approach each other in an open area, and you are sided with one by the story line, so you know that he does not mean to fight.  But what of the other?  You look for some gesture or movement to suggest intent.

Now to lay your weapons down is a wrong move, as it might be taken as a move to surrender, meaning that the stranger then advances with his weapons at the ready in case you are practicing deception.  But you hold your weapons in a nonthreatening manner, likely raising one arm, the right one, skywards to show a greeting and a certain openness, or no attempt to provoke.  You may also nod your heads, which is fairly common for a sign of agreement.  And you slowly circle about each other if you both merely intend to pass.  if one has business with the other, such as a possible trade, he may choose to put the object to trade on the ground and step well back, to indicate he wants the other to come forward.  Words are not absolutely essential in basic communications.  The acts of nodding, raising a hand in a partial greeting, saluting, and staying out of each other's way or space carry forward because they are fundamental to our understanding of communicating with each other at even the lowest level.

You've heard the expression of Act Accordingly.  This is what we are doing.  Now we have to share our knowledge of communications with the machines that we build, and thus they have protocols for identifying whom they are, recognizing the other, performing what we call a handshake, showing a need or interest in information exchange, and alternatively  showing an ability and willingness to accept information in turn.  It's this fundamental behavior that is expected and can be sought out, and even be used as a means of going further.  For humans, we could attempt to learn a bit of each other's language.  For computers, they can be programmed to probe a what is inside the other, or what is going on between computers communicating with each other if seen from the sideline.  That is the need for protocols that also puts us at risk where networks are concerned.

---

### Post by oldefoxx on 2010-01-12
A point or two to ponder is: (1) What other identity might the RTL8187B adapter go by? And (2) How do other distros of Linux fare when it comes to working with the chipset involved?  A part of that answer was found in a post where someone claims that the Realtek RTL8187B is also known as a netgear wg111v3.  Then you might initiate a search based on Linux OR Ubuntu rtl8187b OR wg111v3 driver, and see what turns up.  One of the early responses was that the wg111v3 is well supported in Linux MINT Gloria, and that means a download of the ISO and CD burn might give me a chance to verify for myself.  If it works, I can attempt to backtrack for more info on the netgear solution for Linux, and even see if modprobe will turn up something new in this regard.

The hurtle is, I'm just not there yet, and I seem to be the only one that is willing or able to push it that far.  My lifelong career in support taught me that persistence is often the only way to go, or just give up.  I don't regard myself as being a quitter, when even a narrow path can be perceived through the thicket around me.  And if I have to, I will make my own path rather than just give up.

---

### Post by oldefoxx on 2010-01-13
Back again.  No surprise to any of you, I'm sure.  Ran into a wierd problem yesterday.  This is with Ubuntu 9.10.  Hadn't had the Gateway up for awhile, what with the wireless stuff and the notebook.  Started up fine, then the Update Manager notified me of stuff available.  Told it to go ahead, and it did 260 updates.  That's a bit extreme, even in my book.  Then it wanted a reboot.  So I did it.  But then none of the five 9.04 and 9.10 installs on that PC would boot, each reporting a file missing.   So that is something to straighten out.  Wonder what really happened?.

The another wierd problem with the notebook and 9.10.  Decided to download some ISO files related to stuff I want to check out with regards to going Wireless.  Only when I tried to save the files, nothing happened.  No download started.  Did this repeatedly, and none of the ISO files would download and save.  Did find that I could try to open in a new window or new tab, and sometimes get offered an Open with [browse...] choice.  I hadn't tried this before, and it took awhile to run down brasero as being situated in the /usr/bin folder.  But that worked, up to a point.  I got the image down, but as soon as I burned a CD or DVD, the ISO was deleted from the hard drive.  To get around this,
I held up the actual burn, or delayed the choice of making another copy, and went ahead and copied it to another place on the hard drive, then finished the burn.  Real odd, and it took time to come up*with the workaround.

So what did I get out of all this?  Well, at the moment I am running Linux MINT 8, called Helena, in the LiveCD mode.  What makes it work so well when it comes to the wireless adapter that is suppose to be the clone of the RTL8187B?  Nothing evident at the start, and it does not seem to do any better than 9.10, but then I stumble on two things:

The first is that with the Wired connection up, under Network it shows Windows Network, and under that, WORKGROUP.  Now for Linux to show Windows Network in that manner, there must be some effort on the Linux distro developers to lean towards working with PCs in the same network.  I mean that is probably a good sign.

The second thing is that with the Wired connection down, there is nothing evident concerning the Wireless side, just as blank as found under Ubuntu.  It doesn't come up of its own.  So looking further under the provided Menu, I find a Control Center link, and using that, I get to a page where the left side lists Network and Internet, so I go there.  Guess what I find in the center column at the bottom?  It says "Windows Wireless Drivers".  Yep, here is an evident way of calling on ndiswrapper to just install and work with a Windows' driver, and we've talked about that approach before.  I mean it works, and we could do it,
but there are those trying to make it all happen with just code for Linux, It's suppose to have happened already, but I can't seem to get to the point of establishing that for myself.  But I think it answers the question about what they did with Linux MINT for it to handle this problem.  Of course the good thing is that they added tools to make it much easier for everybody to get the job done.  Hmmm.  Well, I've got some more disks to check out now, but I will be back.

---

### Post by oldefoxx on 2010-01-13
Back already, and with something slightly remarkable to add.  I tried another CD, which turned out be another Linux MINT 8, but I went ahead and booted to try something else.  Nothing major there, but I decided to use Google and shoot for another possible linkup, using linux netgear rtl8187b driver and see what popped up.

This is what popped up:  [http://linuxwireless.org/en/users/Drivers/rtl8187](http://linuxwireless.org/en/users/Drivers/rtl8187)

And it is quite informative in some ways.  It list the Realtek chipsets, what crosses to other types, what is supported, and what is not supported. Further, it shows that the prior cross from Netgear to Realtek may have been in error, because it gives a different line up over several models.  It also has a link I want to check out.I would loved to have had this in hand a few weeks back.  Let's see what it does for me now.

Well, here is a good page.  Gives some history as well, and the need for more contributors - code, documentation, bug chasing, the typical things.  [http://rtl-wifi.sourceforge.net/wiki/Main_Page](http://rtl-wifi.sourceforge.net/wiki/Main_Page)

That then takes you to another useful page, about installing rtl-wifi and how to do it.  [http://rtl-wifi.sourceforge.net/wiki/Installing](http://rtl-wifi.sourceforge.net/wiki/Installing).

That should be enough for some of you to try something different now.  Whatever you try, how about reporting back here to let the rest of us know what works, what extra steps to take, and all the good stuff.  There are no heros or incompetents involved, just some people looking for their own answers, but it can pay to help each other.

Gotta go.  There are still more CDs to check out now.

---

### Post by oldefoxx on 2010-01-14
Okay.  One of the DVDs I burned was NST (Network Security Toolbox, 2.11.0), about 1.2G in size.  Got this from SourceForge, and did a LiveCD boot of it, but it isn't clear what tool does what, and there are a lot of included tools.  It's going to take some study to get anything done with it.

The other DVD was Back Track 4, 1.3G in size, which some refer to as the best tool for the purpose out there.  Again, study will be involved.  Did note that the core distro was Kubuntu, which ought to make some of you happy.  LiveCD boot of it went well too.

I'm thinking, okay I have two more distros to accomodate, and I might end up putting them on the Gateway.  Won't serve well there though, because it is not wireless in and of itself.  I could add a PCI Wireless Card, or I could go USB to Wireless, but it would really be just to play with the software until I get a bit of a feel for it.  To go to the notebook instead and yet keep what I already have on it, I would probably have to replace the 250G drive with a 500G, or at least a 320G.  Not ready to do all that yet.  Guess I will play with the LiveCD approach for awhile instead.  Yes, much of what we start with is free in nature, but at some point you still end up feeling that you have to buy something more.  At least it is bonefied hardware that you are thinking about buying though.

---

### Post by oldefoxx on 2010-01-14
Man, this is way too much!  If you followed a link given, you would see that the claimed relationship between NetGear and RTL8187B is not supported.  Instead, it shows a releationship to an LevelOne product.  So you decide to take that model and do another search, and it may take you here:  [http://linuxwireless.org/en/users/Drivers/zd1211rw/devices](http://linuxwireless.org/en/users/Drivers/zd1211rw/devices)

This is a list of wireless devices with the brand name Zydas.  What it is doing is giving you another cross reference between a zd1211 and other brands and models.  And this is not a short list either.  Supposedly, these are all supported devices. Now if you make a cross reference of a number of cross references, you can add some more matchups as well.

So here is what this cross reference says about Zydas matchup with LevelOne:

LevelOne WNC-0301USB v1 zd1211 0ace 1211  	 	 	
LevelOne WNC-0301USB v2 zd1211 0ace 1211

Wow!.  Just find a driver for zd1211 and you should be good to go, right?

Hmmm.  Pay attention to the note at the bottom of the list:

Notes

1
    Multiple versions of the device exist that may not be clearly distinguishable but use differing chipsets, not all will be supported. 

Now what the heck does that mean?  This refer to what is in column B or in column D?  In other words, which device is being discussed here?  If you look down the whole list, you will see that there are only two devices being referenced:  zd1211, and zd1211b.  This suggests that there are only two models involved.  But then note Columns E and F.  These do change more often, suggesting variations in what is called zd1211 and zd1211b, and that might be what the note above refers to.  So even though the list starts off giving you the impression everything is supported, the note at the bottom suggests otherwise.  And there is no clarification between which is what.  Of course the note might refer to what is in the first two columns instead, and that might suggest that their device works with some of that vendor's models with that nomenclature, but not all, as no vendor is bound to keep using the same chipset for the life of the product.

So did we gain anything here?  Who knows.  There might be something to play with, like looking for a driver for a zd1211,or possibly for the model matchup in Column B, but it really is guesswork at this stage.

One of the great gains that Windows made was the introduction of a Plug and Play system that works pretty good.  That it works at all is an admission that Microsoft had considerable power to get OEMs to submit their devices for testing and certification.  To get certified, your device had to also be distinguishable from the herd of other possible devices that might be attached. The drivers had to be installable and to work as intended, so taken altogether, it was a good plan.

Before plug 'n' play, you had to deal with one item at a time, and make a lot of choices, hoping that it would all work together.  I used to work on a Control Data Corporation (CDC) system marketed to the U.S. Navy, and they instigated a unique 12-bit code for system devices so that any computer could address itself to any device and see if it were currently attached, and if so, make it do things.  It was rather neat, easy to work with, and I could not really understand how other systems could work without something similar in place.  The trick there was just to wire it up, get it to work, and leave it in place.  Not very flexible, really.

So plug 'n' play was a big step forward.  Now Linux seems to be getting much better at distinguishing device hardware, at least for commonly used devices, and that is a good thing.  But it is lacking with regards to other types of devices, and if the OEMs are not kicking in with the necessary drivers for Linux, there is a big question of what to do about it.  And there is even a question of what to do about a device that reportedly should be working, but isn't.  Windows will at least show you what device driver it is trying to use, and give you an OEM list to choose from in an effort to find a better driver, plus you can use an OEM supplied disk or search on the internet for a better driver.  Oh, and it will tell you if it thinks the device is working or not, but might show a question mark to indicate that it is not responding as expected to certain requests.

As far as I can tell, getting Linux to tell you which driver it is trying to use with a given device just isn't included. So how can you judge if it is the right one or not?  And how can you distinguish what you already have from something that might be better?  And on top of that, how would you relate to Linux that you want to try this driver in conjunction with that device?  From what I've heard in the past, Microsoft spent an enormous amount of time and money trying to thread together a process that it could program, where it had the best chance of matching drivers up with devices on its own, and only when that fails are you offered other choices of how to proceed.

I see the wireless issue here as a deep Linux core issue.  I'm way more experienced than most in dealing with hardware and software issues, and if I can't work it out, what chance the average Joe?  I put forth what I find as I go along for several reasons:  First, I want to get it fixed.  Second, I'm trying to help others do the same thing.  Third, I'm looking for some effort from someone who is deep into the stuff and who can pull it all together, because we all could learn from that.  And fouth, if it just won't come together, I consider that a strong indication that Linux just cannot cut it in a world where Windows dominates.  I hate to say it,
but that might be my final conclusion if nothing improves.  I'm not saying this on my own part, as I am totally fed up with where Windows has been and is going, and I will find some part of the linux world where I will be comfortable enough, but I can't speak for others.

---

### Post by oldefoxx on 2010-01-17
Well, the news is not good.  In a final moment of desperation, I plugged the ExpressCard Wireless-N adapter into my notebook to see what I could see with it.  It registered internally, a light on the adapter would come on, but nothing I did with either Wireless adapter would let me connect to the Wireless-N router with Radio On and running unsecured. Oh, I might get a brief message saying that it was connected, but absolutely no traffic.

I am going to have to reiterate something here.  It's my estimation that over 95% of laptop and notebook owners are going to want or need to make a wireless network connection sooner or later.  The other five percent don't get out with their PCs at all.

There are so many different Wireless adapters, several standards, and an array of drivers out there, and to work out what will work with your machine can be really hard to determine.  In my case, hasn't happened yet.
There is no one Linux source to go to for answers to begin with, and so far as I've been able to determine, none of them has anything much in the way of answers.

So how about built-in tools to deal with the hard part?  Which tool does what, in which order to use them, and finding out how to go the next step are all left unanswered.  Even getting down to the command line shows little promise of resolution.  I get told one place that not specifying a SSID gives you access to public access spots, but the network tools demand that you include an SSID anyway.  Two exceptions might be "" for null or no SSID, or ANY for any SSID.  Seems that using either is taken literally.

Nothing fits together.  Do this.  Do that.  But neither does anything.  Where to go next?  No one seems to know.  Either it worked right out of the box, or you are left buried up to your eyeballs in sand.  The fallback either seems to get another Wireless adapter, one that should work with what you have, or go with ndiswrapper, which apparently works more often than not, but is not something that just happens on its own.  First, you have to find out that there is this alternative, second you have to find it, third you have to find the right Windows' driver, and then fourth you have to put it all together.

This is really not good news.  You want to spread Linux, you have to make it transparent and user friendly.  Not being able to get to the internet is not a sign of being user friendly.  Not being able to find a way to do it, even with the internet as a resource, is not just unfriendliness but... well, I am not sure what to call it.  I best say nothing to offend someone among an array of volunteers.  Maybe it relates to a lack of adequate volunteers to cover everything.

I'm just trying to show a spotlight on what I regard as a significant gap area with not just Ubuntu, but with Linux in general.  I could not find a coherant answer to all this, but if I do, I will be back.  My hope to pull some involvement into this area with this thread has proven to go no where, and I am going to leave it at that for awhile.  Meanwhile, it is definately UNSOLVED and UNRESOLVED.

---

### Post by oldefoxx on 2010-01-18
I rather thought that I would be off this thread for some number of days, possibly weeks.  But in digging around for another attack, which turned out to involve dmesg, I used it, went gradually through the long log that it provided, and then sought an answer to why dmesg was reporting that wlan0 is not ready.  Yep it was hidden in the log, and I needed some reason and method to find it.

Turns out this error was reported different places, not the same Linux distro, but was reported as a bug for Ubuntu once past Hardy.  Reading the bug report, a possible solution was proposed, which essentially involved using the following command in a Terminal window:

sudo apt-get install linux-backports-modules-hardy-generic

Of course Ubuntu 9.10 is known as Karmic Koala, so I changed it this way:

sudo apt-get install linux-backports-modules-karmic-generic 

That fetched a package, I said yes to continue, and I suddenly have a connection by Wireless to my Wireless-N router.  Question is though, why should there be a connection when the router is set with Radio Off?  Guess I better work on getting that encryption going pretty quick.  There are other indications that I may only be at Wireless-G, and statements made that Linux driver support of Wireless-G may not extend beyond WEP.  But that there is a wpa_supplement that can be added to change that.  So much more work to be done.

My guess is that the problem with 9.10 got recognized early on when it comes to some Wireless issues, but either it was not a priority or there were other reasons to put it back for later release, I don't know.  So you have to go fetch it yourself.  Meanwhile, who's to know that there is a problem as well as a fix?  There is just too much study involved in dealing with an issue like this, and yet apparently the answer might be right there, even if not before you.  Maybe there is a finite limit to what gets updated by the Update Manager.  I mean not everyone uses Wireless, and not everyone is having a problem in this area, and most likely the Update Manager is only told what there is in the Main Stream, and there is apparently no way to ask the Update Manager to search for an update or replacement for a driver that is not in service already.  The included Package Manager?  I don't think it knows what drivers are, just packages.  So what's the means of culling for drivers and seeing what might be a better fit?  Maybe nothing.  Seems a lack, somehow.

---

### Post by oldefoxx on 2010-01-18
I need to get on to bed, but I have to pass this along first.

Okay, you know that I got the wireless working.  But now I want to try it under  VirtualBox and Windows.  So I go there, and under Settings, I've given the Guest OS access to my Realtek adapter, which is under USB devices.  Only neither my host or my guest can then get to the network.  Hmmm.  What does this mean?

Having worked with VirtualBox for awhile, I know it shares the network connection with both host and guest.  But it is far less generous when it comes to external hard drives, which are connected by USB.  Either one or the other.  Could that somehow be part of this?  So I go back to Settings and disable sharing of the wireless adapter.  I try Firefox under the host.  It works.  I try Firefox under the guest.  It also works.  Not sure of the mechanics of this, but it works both ways.  I still have the Windows driver in place on the Windows guest side, and the driver accepted by Ubuntu on the other side (I might look tomorrow to see which one it decided to use), so all I had to do is leave that setting alone in VirtualBox.  By setting it, I know VirtualBox robbed the host of access to it (what it does for external drives), but why the guest then could not use it is something I don't quite understand.  There is always something, right?  We can expect that.  We can also expect not really understanding it as well, that is just the way it is.

---

### Post by oldefoxx on 2010-01-18
So somebody in the back is going to shout, "Mark it SOLVED already!".  Afraid I can't. After a bit more use, shut it down, went to bed. slept well, cleaned up and had breakfast, and sat down and turn the notebook on, and guess what?  Back to "Unknown error 132".  Remember that?  That was when it seemed apparent that the adapter was not recognized.  Used the Edit Connections feature, and had to add back the MAC address which had cleared out.  Connection had originally gone by the adapter name, which it picked, and now was showing the Wireless Router name.   Noted that it looks like the adapter driver had been switched out and now was using RTL8187, which may or may not work with this adapter, depending on what source you are reading.

So what tools am I offered to deal with all this?  Apparently some command line things that I can try, some of which actually seem to help, at least for a time.  Or maybe it is the combination of doing things that finally pulls it together, but it's never clear what the combination is or what order seems to work best.

Can't be the Network Manager, Network Tools, Network Connections, or Network Proxy menued items.  They hardly do anything, and don't even seem to work together.  Like there is no way to tell the PC to try this connection now, or disable one connection and try another. You can't find a One Thing Does All in this game for Wireless, and it seems too easy to defeat the automatic setup efforts.

In fact the Network Manager is such a wimp that it does not appear on the menu, can only be found on the task bar (if you are lucky and it shows well enough to be seen), and doesn't really do anything except shift responsibility to Network Tools or Network Connections.  The only thing it does on its own is show you if it is trying to make a connection (whirly thing over the icon), or whether the network and/or wireless are enabled to connect (but it does not allow you to change either setting on its own, and being connected does not mean traffic can flow here).

I have found reference to replacing the Network Manager with wicd, and that it supposedly does more and better.  I did download it and try it, but when I did, I guess I was still so far from getting a working connection up that it did not seem to help.  Maybe I will give it another try.

There are several really good sites out there that seek to explain the mysteries and quirks of wireless when it comes to Linux, but they get too deep into the history involved.  I just want a simple process, a flowchart if need be, of what to do next after this step or coming up onto this symptom or failure.

You know, with the four GUI tools provided, there is none that you can tell "try this connection now".  What are you expected to do, just wait until it eventually decides to do it on its own?  That makes no sense.

Even dumber (in my mind), nothing can be made to work unless the user fills in all the blanks.  You mean I have to tell wlan0 which MAC address to tie itself to because the software can't probe and figure it out for itself?  That is stupid,  If I have two adapters, it should just add a wlan1 to the mix.  At no time, as apparently occuring out there, should the software decide to tie the wireless adapter to eth1 instead.  Ethernet and Wireless do not work the same way, though they do serve the same purpose which is to carry traffic.  But calling it eth1 means misidentifying it within the system, so you know it won't work right.

The other false premise here is that the user will know what to put in those blanks.  Let's call the Wireless Router an Access Point, or AP. You are trying to set up a connection, and it wants a name.  Is it for the adapter in here, or for the AP?  They are both devices, both given names, but which one is being asked for?  How about the MAC address?  Is that for the internal device or are we talking about the MAC address in the AP? It could be either, depending on what it is to be used for, handling the transmitted traffic or the received traffic.  It can't be both, because the addresses are different and only one is being asked for.

What is the MAC address for my adapter?  This thread discussed that matter previously, so I won't repeat it, but many users will have no idea of what is being asked for.  They might even think: "Is this like the McDonald's a few streets over?  Why would they want that address?  No place for the city name or anything else.  Maybe that's not it.  How the heck should I know?"

There are people that walk around this stuff all the time, and for them, it is easy.  If they forget or are not too sure, they know whom to ask.  What they really forgot is that it isn't like that for the rest of us, we are just getting to it, and even to attempt to walk around in it is difficult.  We did not come here with the expectations of a constant, ongoing struggle to get something dealt with, and it does not sit well when you think of all those that can't even manage to get this far.

This is, ultimately, what will keep Linux from gaining widespread acceptance.  There will come a point that for Linux to succeed, there is going to have to be gurus in residence to assist the users when they cannot do for themselves.  Linux can mask itself all it wants to try and appear user friendly, but it's the failures to really get it together that will stand out the most.

---

### Post by oldefoxx on 2010-01-20
As if to point up my last post, I've been having to deal with separate issues in my installs on all three PCs, preventing me from even checking if I could get on the Internet until a few minutes ago.  So what's my basic problem here?  I think I may know, or have an idea about the cause, but it is not going to be easy to check it out for sure.

Let's start with this.  I discussed how I finally found a way to get it to work a few days back, then ran into a problem with it looked like VirtualBox was doing something to mess it up, but how I then found that if I turned off a USB setting in VirtualBox it worked fine for both the host and for the guest.  That was great.  But it had come apart when I tried to get back to it the next day.  This has not resolved itself yet.

It made me think though.  VirtualBox is treating the adapter as a USB device, which by its interface it is.  But in what it does, it is quite a different creature.  But let's go back in time a bit.  First, many users of VirtualBox, and there probably are not a whole lot, are not employing the USB support capability in it, and in fact may be using VirtualBox OSE, which I believe still does not support USB at all.

So obviously, if it is somehow related to VirtualBox, there is an excellent possibility that very few people are vulnerable to this, because there is only a small chance that they are using a notebook with an adapter that is employing a USB interfaced Wireless adapter.

So I could be in extremely small company if VirtualBox is tied in as well.

Now here is the next thing.  I've always set up Ubuntu, got the updates, installed VirtualBox, and added the guest VDIs before I attempted to do anything else, including trying to enable Wireless.  For one thing, I only recently got a Wireless Router to interface with.

What I am saying is, maybe my order of doing things has caused this problem to surface and seem unsurmountable for so long.  Maybe if I had done some things in a different order, and tried to get Wireless working at an earlier stage and succeeded, I might have noted when Wireless quit working at a later stage, like when I installed VirtualBox.

I'm not ready to say that VirtualBox is the problem here, but I am going to have to go back and choose a different path forward and see if Wireless does what it is suppose to do after the initial install, and then retest Wireless after I do other things, so that maybe I can make a real association of cause and effect.

Now you do not just do a wiz pop bang in going through a whole install and setup process, and adding in tests phases make it longer.  And obvious at this point, the only wireless USB adapter I have is with the notebook, meaning what I need to do is going to put a heavy demand on it.  Gee, now if I had just bought that... well, what do they call them?  Anyway, if I had a Dongle Wireless USB Adapter, I could use any of the PCs for this phase, even two of the three if I include the notebook as one.

Could I just do without VirtualBox?  Hey, that's the center of my game plan in going forward.  It is an excellent game piece, and getting better and more flexible, and I would go the other way first.  But let's see what we find out from what I have first.

---

### Post by oldefoxx on 2010-01-20
Okay.  At this moment, have notebook with Ubuntu 9.10 with all updates to the present.  Was using wired network connection.  Only concession:  Using wicd in place of network-manager and network-manager-gnome.  Maybe not necessary, but not real impressed with network-manager as reported before.

Decision:  Go for a wireless connection.  Sees wireless router fine.  Make connection.  Connection made.  Disconnect wire,  Disconnect noted.  Use Firefox to get here.  I'm here.  Wireless is working.  What does wicd say when I hover over it?  Power at 64%.  That's got to be off, there is only about 3 feet distance to wireless router.  Point is though, I am connected. Now do I go straight to adding VirtualBox or what?  Let me think on that.  Might go the other way (to other install with VirtualBox first and see what that is like).  Might call this progress though.

On other install now.  Again, Ubuntu 9.10 and patches applied, but with VirtualBox and still with network-manager.
Wired connection in place, but let's try setting up wireless.  Network manager not much help, but does see Wireless Router.  No traffic though.  Try putting wire back.  Still cannot connect to network.  Go into VirtualBox and remove settings for USB.  No help.  Exit out of VirtualBox.  Ah, that worked, got wired connection now.  Installed wicd in place of network-manager.  No change. Seems I have to reboot maybe?  Have wired connection.   Somewhere in here I finally exit out of VirtualBox.  Now able to get Wireless going.  Unplugged wire.  Still connected to network.  So I think it is VirtualBox, but it could be other things at other times.  Guess time for a VirtualBox bug report.  Can't blame this on Ubuntu.

---

### Post by oldefoxx on 2010-01-21
Alright, here is what I have to report to date.  During all this action, the Wireless-G RTL8187B internal USB Lan Adapter has been able to get on line and work fine.  I've not had to revert to the wire connection once.

Fresh install of Ubuntu 9.04
Performed all Updates
Updated to Ubuntu 9.10 via Update Manager
Had to add portion of language support after getting Ubuntu 9.10 in
Performed all updates
Downloaded and Installed Sun's VirtualBox with built-in USB support
Copied two VDI Images back to hard drive from backup
Set up VirtualBox to recognize both Images via their VDIs
Started up one of the Windows clients
Used Firefox from Windows client to access internet via wireless
Also used Firefox via Ubuntu host to access internet at same time
Now writing and posting this thread via Firefox in Windows client.

What I have left to do tomorrow is begin at this point as see what happens when I work with VirtualBox and enable/disable USB via its settings.  However, I have already opened a bug report with the information in hand, and given them the details I have to date.

Here's the thing.  It's fine that VirtualBox wants to separate USB devices like drives, printers, scanners, maybe sound and video feeds so that they don't overlap both host and guest at the same time, but there are some things, like the internet, which are intended to be shared between both, and that means this is a specific category issue for Sun to try and resolve.  If I can find a temporary workaround, then so much the better.

How extensive is this problem?  Hard to really say.  You have to first have some USB to LAN adapter, which could be internal or a dongle, and then you have to use Sun's VirtualBox and enable USB support for some client.  That seems pretty certain,  Can you avoid causing this problem, or can you back away somehow if the problem becomes evident?  That I don't know yet.  I hope to find out.  But from what I can see so far, this could happen with a desktop PC having the same software on it and using a USB plugin to get to the internet, whether wireless or ethernet.

---

### Post by oldefoxx on 2010-01-21
The wicd software really does seem better than relying on network-manager.  You just have to add it by using sudo apt-get install wicd*,
and it will remove network-manager and network-manager-gnome automatically as it installs.  The icon on the toolbar is much easier to see, and it includes the capability to do either a connect or disconnect as you choose, and you can even indicate whether you want to do an autoconnect or not.  Oh, and it gives you a percentage of signal strength indication as well.

Things going great so far on using the wireless adapter.  Have got VirtualBox up and running, the clients set up, even have USB enabled for the clients and no problems so far  When I say enabled for the clients, I just mean that VirtualBox has the boxes checked, but no wireless devices assigned to the clients yet.  But definately progress.  Just wonder if it somehow relates to the order in which things are done with the install process.  This time around installing VirtualBox was last.

Anyway, some more things to try now.

---

### Post by oldefoxx on 2010-01-21
So far wireless is still up in both the clients and with the host.  No wonder some people had a real hard time buying that i had so much trouble originally.

Oh, I do have a problem though, but with one of the Windows clients.  After booting it up, got notification of a patch or update availability on the lower right toolbar.  I went ahead and installed it.  Guess what?  On my next boot up with that client I got hung in a message loop that I either did not have a paging file or it was too small.  It told you how to increase it, but not how much to increase it to, and I could not get far enough in the boot process to do anything to get past it.  So it is stuck in a groove now, with no apparent way out.  And some people want to stick with Windows anyway?

Fact is, I sent an email to family members last night excusing myself from repeated laborious efforts to recover their machines aand get them back to a point of being more like they are use to, but knowing full well it is just a matter of time before they are going to try and have me do it again.  And again.  And so on.

Point being that I can offer a much better fix involving Ubuntu, and they need to listen to me in that regard.  If they don't, and won't let me put my very best effort forward, then they just need to turn and look for help elsewhere.  My solution for all of them is Ubuntu host, VirtualBox VM manager, and Windows with apps as clients.  This works so well, but they have shown no interest at all, and I'm just tired of the whole Windows' game.

---

### Post by oldefoxx on 2010-01-22
Wireless still working good.  So summarize what I've worked out:

Might need wired connection at this point:
Install Ubuntu.
In Terminal, do sudo apt-get install wicd*.  Enter y and enter.
Get Wireless up and running.  Might have to reboot first.
Disable or disconnect wired connection.  This will test wireless going forward.

Now running with wireless connection:
Run Update Manager and get Ubuntu up to date.
Search internet for the following: sun virtualbox download linux.  Find link where you get the version for your version of Ubuntu and cpu.
Download VirtualBox to install it.  After install. check internet connection.  Make sure is still up.
Under System/Administrative/Users and Groups, Click box to make changes, then Manage Groups, then scroll down to vboxusers.  Click on that.  Put checkmarks in boxes beside anyone allowed to use VirtualBox. 
Reboot.

Sun VirtualBox added under Applications/System Tools after reboot.  What else is shown within menus controlled by settings in System/Preferences/Main Menu.
Make sure Wireless is running and able to connect.
Add New virtual clients in VirtualBox.  Port or create new VDI instances.  Check settings for each, whether USB is enabled for client or not.  Make sure wireless keeps working for you throughout.
You got real clients installed, Start them up and check their ability to get to the internet.  You should have it both ways, with the host and the client able to use the internet independently.
If you can do all that.  You are almost set.

Some last things for Windows clients though:
Might pick a real low number of amount of base RAM to use, like 168 MB.  You can go higher, meaning better performance from client.  But it is all coming out of real RAM, so too much is not good.  You will see a warning if you go too much anyway.  I'm currently using 512 MB.

Just found out that Windows install took my 512 MB and multiplied it by 1.5 to reach 768 MB, and set upper and lower ranges of Virtual Memory accordingly.  One new Windows patch installed, and my Windows won't boot, just loops where it reports not enough page file space or missing page file.  No way around it, and Windows does not come in a LiveCD edition.  Have to boot client with Linux LiveCD, and see if I can find a way to deal with it.  Tried cat pagefile.sys pagefile.sys pagefile.sys > pagefile, then mv pagefile pagefle.sys, and the boot effort goes further, but still same message.  This is a nightmare, as only Windows can make it.  you diehards, you really think that Windows is all that great?

Anyway, this is a warning that you really need to set and verify the Virtual client's settings for Virtual Memory to make sure you are not victumized the same way.  I keep reading that the lower limit should be about 1.5 times actual RAM, and the upper limit might ought to be twice as much as actual RAM, but no more than 4095 MB for Windows 2000 (it will not let you go higher, in fact, but you can set it higher via the Registry).  Later versions of Windows will of course be somewhat different.

Now how do you change virtual memory settings for Windows?  One place shows you how to do it through the Registry, but with Windows not starting, that is not much help, since you can't run Regedit.  Others guide you to Start/Settings/Control Panel/System/Advanced/Performance[Performance Options/Virtual Memory[Change]], only that is such a handful, they don't bother to give you the whole of if.  No good here anyway, since I can't get that far in booting up.

Point to be made, anyone convinced that Windows is the better or easier way to go simply has not had to really deal with some of the complications that come with using it.  The Vendor took care of it beforehand, or the Repair Shop took care of it okay for some fee, or some friend of yours managed to deal with it for you, probably at no expense to you.

Linux is the operating system that is hard to beat, and even the Mac OS owes something to the inspiration that has gone into Unix and various flavors of Unix offshoots.  And though I've tried various flavors of Linux, I still prefer Ubuntu because of how easy it is to get to and do most anything.  Other Linux Demos probably do as much and more, but Ubuntu makes most of it easy to find and deal with.

And the price is not only hard to beat, but to do better, someone would have to pay you, instead of you paying for it.

---

### Post by oldefoxx on 2010-06-14
For some reason, as mentioned elsewhere. the move to 10.04 which looked real good for a couple of weeks. got me into trouble.   I even found that the ability to go Wireless with the notebook had gotten lost.  I went back and found this thread, followed it through, found where I had done certain things, and as with 9.04, the wireless ability was restored.  So it still counts.

A bit further on, I read a post that someone made objecting to me making a personal blog or journal of all this.  This is just suppose to be for questions and answers, and I was not with the program.

Yeah, I ask questions or post problems, and how long am I suppose to just wait for someone else to deal with it?  Some of these threads never get answered, and I am not going to just sit on my hands and hope someone else does it for me.  I will try to do it myself while waiting, and whether I make progress or not, everybody is entitled to know what is happening.

Besides, if somebody doesn't post to a thread, it just slides to the bottom of the heap.  It may stay active in theory, but who is going back a few hundred or thousand threads to find it?  Someboey come up with a similar queston later on, then the attention shifts there.

So in a way, I think some of you are missing what a forum is about.  It is a matter of open discussion, and we decide when we have participated enough.  Your Q: amd A: approach should be reserved for Askl the Experts.

---

