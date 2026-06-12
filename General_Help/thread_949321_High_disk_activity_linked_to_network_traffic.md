---
title: "High disk activity linked to network traffic"
date: 2008-10-16
forum: General Help
---

### Post by smi402 on 2008-10-16
[SOLVED]
I have recently noticed that my disk activity is on for several minutes at a time even though no main applications are running and almost all the processes reported in the System Monitor are "sleeping". I have found that this high disk activity is directly associated with readings on the Network History graph in the System Monitor. It appears that the disk activity light is out when the network history is around 0 KiB/s, but when this jumps up to around 6 KiB/s receive and 3 KiB/s send (both still low values) the disk activity light comes on and virtually stays on continuously until the network history graphs fall back to the baseline. This goes on in cycles - perhaps a minute or so at the baseline with no disk activity followed by 2 to 5 minutes when something is being received and sent through the network and the disk is going crazy. Very little memory is being used, there doesn't appear to be any swapping going on and both cores of the CoreDuo CPU have less than 15% usage. The disk is less than 50% utilised and is formatted ext3. I am running Hardy 8.04 updated to Oct 16 2008 and the 2.6.24-21-generic kernel (I had the same problem on the 2.6.24-19-generic kernel). This is a desktop machine with Gigabyte GA-P35C-DS3R motherboard. onboard Realtek 8111B network connector, 2GB DDR2 memory. It is connected to the internet through a Billion ADSL2 router that has a firewall running. This problem is not showing up on another similar machine connected to the same router but running the current updated release of Intrepid 8.10 amd64.

Shutting down NTP, Samba and Apache2 have made no difference. I also changed the LAN static address but this also made no difference to the disk activity. I would really appreciate some thoughts and advice on this problem as it is flogging my disk to death in its present state, and I am also concerned that I may be being hacked as I can't account for the network activity that is showing up in the System Monitor.

Trust someone can help.

Frank. :(:confused:

---

### Post by sparky-steve on 2008-10-16
By any chance have you mounted any network drives on this machine, and do you have any kind of indexing software installed (such as beagle).  This sounds very similar to a problem I had very recently, and it was beagle indexing over 2TB of data on a server I had mounted.

Just a thought?

SS

---

### Post by smi402 on 2008-10-16
Thanks for your thoughts, Sparky-Steve. I don't have any NFS drives mounted on this machine at present and I don't have Beagle installed so I don't believe these can be causing the excessive disk activity or the network throughput. After checking through some other threads related to excessive disk activity I have also removed Wine and Wine applications from the system. None of these have reduced the disk activity or the network throughput that seems to be directly causing the disk activity.

Can anyone recommend some Linux application that would enable me to "snoop" on the network traffic so that I may be able to trace what is causing it?

Frank

---

### Post by sparky-steve on 2008-10-16
Hi Frank

When I was scratching my head trying to solve my problem, various people on my local LUG mailing list told me that wireshark was the God of all packet sniffers.

I actually resolved my problem just before installing, and since have not felt the urgent need to install/play, but here's the link for it:

[http://www.wireshark.org/](http://www.wireshark.org/)

If it works for you, perhaps you could post back. Many people have said it's in their "top 10" for linux network tools.

Hope it helps!

Steve

---

### Post by smi402 on 2008-10-16
Thanks again Sparky-Steve. I installed Wireshark from the Ubuntu repository and used it to capture the eth0 traffic. The UDP Stream analysis of the packet is:

```
J............mail.............;.@.A.ROOT-SERVERS.NET..NSTLD.VERISIGN-GRS.COM.w.2...........:...Q..............mail..................mail............
..@.A.ROOT-SERVERS.NET..NSTLD.VERISIGN-GRS.COM.w.2...........:...Q..............mail..................mail.............|.@.A.ROOT-SERVERS.NET..NSTLD.VERISIGN-GRS.COM.w.2...........:...Q.+............mail.....+............mail...............@.A.ROOT-SERVERS.NET..NSTLD.VERISIGN-GRS.COM.w.2...........:...Q.

```
Given Verisign is a leading electronic banking organisation I wonder if this suggests the machine has been hacked and used to interrogate the Verisign servers. I'm only guessing - is there someone out there who may be able to better interpret this output from wireshark?

In the meantime I'm shutting the machine down overnight (Australian time) and will check again tomorrow morning.

Frank.

---

### Post by smi402 on 2008-10-23
This problem has now been fixed. Both the disk activity and the network traffic were the result of my small network being hacked and my server being hijacked. This was caused by a Windows XP machine on the network becoming infected with Event Horizon, a backdoor Trojan that encorporates a Remote Access Tool (RAT). This is a particularly nasty piece of software that enabled some outsider to disable the firewall in my router and start using my Ubuntu Hardy Linux server to receive stuff and forward it back onto the network (spam, pornography, pedophilic nonsense - who knows what) - hence the disk activity and the up and down network traffic, the rate of which was just sufficient to keep below the radar so as not to be obvious. My router log told me it had been disabled by Event Horizon and the IP address of the Windows machine that did it.

The disconcerting thing is that Norton 360 on the Windows machine told me it was clean. So I ran a scan on the machine with Exterminate It and there it was. Cleaned that up but still could not keep the firewall enabled - it would revert back to disabled after a few minutes running until I also changed the password on the router. Then went through and closed down ports - again a few of these turned the disk off but it started again in a minute or so as I guess traffic was transferred to another port. Eventually only had Port 80 on - turning this off stopped the disk activity but of course it also closed down internet access so is not a solution. Bit the bullet and pulled the OS drive out of the server, put in a clean one and reinstalled Hardy. Changed all passwords for the new installation and everything seems to be OK now. Was reluctant to do this since I was going to do a clean install of Intrepid on this server when it is released in just a few days - but, I guess I will just have to do yet another install and then put all the application packages I used back onto the new server. A lot of work. In the meantime I have the infected disk with the Hardy installation on it in a drawer in case the police turn up looking for an internet spammer, pedophile, terrorist or other undesirable.

The lesson - BEWARE - Windows machines on your network can bring the whole thing down unless they have very rigid virus and malware protection. I had believed that Ubuntu Hardy was bulletproof against such attacks, but I guess a network machine infected with this really nasty piece of code can compromise even Ubuntu. I have now implemented stringent network security and ensured passwords on all machines and users have been changed. Also switched from WEP security to WPA on the wireless network and stopped the SSID from being broadcast. Seems locked down fine now.

The other disconcerting aspect was the failure of a market leader like Norton to identify this Trojan on the offending machine. It is interesting to look through the latest AV-Test reports and see how the antivirus and malware software stacks up these days.

[http://www.virusbtn.com/news/2008/09_02]("http://www.virusbtn.com/news/2008/09_02")

To guard against something like this in the future I would love to drop-kick these couple of WindowsXP machines off this small network - with such great software as Ubuntu on the server and desktops and users with MacBook notebooks I see no logical reason for any users to stick with potential threats like WinXP.

The characteristics of the Event Horizon backdoor Trojan are:

[I]Event.Horizon Categorized as:
Backdoor

Of all trojans, backdoor trojans pose the greatest danger to users&#8217; PCs because they give their authors remote control over infected computers. They are downloaded, installed, and run silently, without the user&#8217;s consent or knowledge. Upon installation, backdoor trojans can be instructed to send, receive, execute and delete files, gather and transfer confidential data from the computer, log all activity on the computer, and perform other harmful activities.

RAT
Remote Access Tool. A program that enables a hacker to remotely access and control other people&#8217;s computers. A RAT can serve a variety of malicious purposes, including hijacking and transferring private information, downloading files, running programs, and tampering with system settings.[/I]

---

### Post by Peter09 on 2008-10-23
Hi,
I was interested in your experience and wondered if you had any understanding of how this Trojan compromised your Ubuntu setup? Was it actually running on your Linux system?

---

### Post by smi402 on 2008-10-23
Peter09,

I have been pondering this same question as I had expected that the Ubuntu server would not be compromised. I am only guessing but here are a couple of thoughts:

The characteristics of this Trojan once on a network enable outsiders to gain remote access which is clearly what was occurring. With that I guess it may have been possible to determine passwords by monitoring keyboard strokes or some such mechanism and then get into the machines.

It was definitely the machine running the Ubuntu server (192.168.1.1) that was being used to download and upload to the internet. It was only the disk on that machine that was being thrashed whilst the traffic was going across the internet - a couple of other Ubuntu desktops on the network were unaffected. As soon as I shut down that server the router told me the internet traffic stopped. But, I have been wondering if it may not have been Ubuntu that had been compromised as there was a small WinXP partition also on that disk that I had used to set up and monitor overclocking of the CoreDuo processor. I really do not know but wonder if whoever had grabbed control was actually using the WinXP partition as a virtual machine or something.

I do not want to contribute to a Linux/Windows turf war but I have learnt my lesson so will be very wary of Windows at all times!!

---

