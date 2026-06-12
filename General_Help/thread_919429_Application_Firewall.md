---
title: "Application Firewall"
date: 2008-09-14
forum: General Help
---

### Post by solarwind on 2008-09-14
On Windows, I have used application firewalls like ZoneAlarm which can set internet access on a per-application basis. You can control exactly how what internet access an application gets (access to net, trusted, server to net, trusted for example).

Is there anything like this for Linux at all? At least is there anything I can use to prevent certain applications from accessing the internet?


Or is there a way to make another user and disable ALL internet access for that user? I'm trying to run a program and I do NOT want to give it internet access. Actually several programs.

---

### Post by Neo_The_User on 2008-09-14
KMyFirewall (advanced)

Firestarter (simple and easy)

iptables (complex command line)

I would highly recommend firestarter.

---

### Post by mb_webguy on 2008-09-14
Just to clarify, iptables is *the* firewall for Linux.  Firestarter and the others are just GUI front-ends for iptables.

Having said that, I've heard good things about Firestarter.

---

### Post by solarwind on 2008-09-14
I tried firestarter, but its based on ports and protocalls. I can't chose if I want to block only a specific application from internet access. That's all I need - to block certain applications.

Or if there's a way to create a separate user with no internet access and run certain apps *as* that user, I'm fine with that too. But I don't know how to do this.

---

### Post by Neo_The_User on 2008-09-14
iptables is the firewall for linux except no GUI but it is still a firewall. For blocking certain applications KMyFirewall would be best. Might take a few days to get used to it. 

And yes, Firestarter and the others are just GUI's for iptables except have completly different features.

---

### Post by solarwind on 2008-09-14
> **Neo_The_User said:**
> iptables is the firewall for linux except no GUI but it is still a firewall. For blocking certain applications KMyFirewall would be best. Might take a few days to get used to it. 

And yes, Firestarter and the others are just GUI's for iptables except have completly different features.

So how would I use KMyFirewall to block a certain application?

---

### Post by Yannick Le Saint kyncani on 2008-09-14
Hi solarwind, **there is no such thing for linux** yet.

AFAIK, the closest things available right now are selinux and apparmor.

Apparmor is not supposed to provide per-user runtime rules I think.

SELinux is more complex than quantum physics.

Sorry.

---

### Post by solarwind on 2008-09-14
> **Yannick Le Saint kyncani said:**
> Hi solarwind, **there is no such thing for linux** yet.

AFAIK, the closest things available right now are selinux and apparmor.

Apparmor is not supposed to provide per-user runtime rules I think.

SELinux is more complex than quantum physics.

Sorry.

Ok. In that case, let's say I have a program that I want to run. I do NOT want to give it internet access. What's the best way to completely prohibit only that application from having internet access?

---

### Post by brian_p on 2008-09-14
> **solarwind said:**
> Ok. In that case, let's say I have a program that I want to run. I do NOT want to give it internet access. What's the best way to completely prohibit only that application from having internet access?

Would you please be specific about the program.

---

### Post by solarwind on 2008-09-14
> **brian_p said:**
> Would you please be specific about the program.

The program is irrelevant. Let's say the program was /bin/cat. When run, I want to completely remove internet access to that program only. How do I do it?

---

### Post by Yannick Le Saint kyncani on 2008-09-14
> **solarwind said:**
> Ok. In that case, let's say I have a program that I want to run. I do NOT want to give it internet access. What's the best way to completely prohibit only that application from having internet access?

There is no such way to do that other than using selinux or apparmor (and I have investigated none of them for myself).

Sorry :(

---

### Post by solarwind on 2008-09-14
> **Yannick Le Saint kyncani said:**
> There is no such way to do that other than using selinux or apparmor (and I have investigated none of them for myself).

Sorry :(

Then I'll use apparmor. Thanks for mentioning that to me!

---

### Post by Herman on 2008-09-14
[COLOR=#000000]If you have more than one computer in your network you can use each one to scan the other(s) for open ports. Ubuntu comes with some very good networking software.
Just go 'System'-->'Administration'-->'Network Tools', and clicked on the 'Port Scan' tab.
You need to know the IP number for each of your other computers that you want to scan.
The easiest way to get that is just to go to the other computer and run 'ifconfig'.
The scan only takes a few seconds.
It is possible to detect any open [/COLOR][COLOR=#000000]ports.[/COLOR][COLOR=#000000]
If you find any other open ports you can use this command to see what service they're probably for,[/COLOR][COLOR=#000000] [/COLOR]```
less /etc/services
```[COLOR=#000000]Here are a couple of internet links about which port numbers are commonly used by various services too,
[/COLOR] 
[LIST]
[*][COLOR=#000000][Ports and Services]("http://www.spirit.com/Resources/ports.html").[/COLOR]
[*][COLOR=#000000][List of TCP and UDP port numbers]("http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers").[/COLOR]
[/LIST]
 [COLOR=#000000] [/COLOR][COLOR=#000000]Even better, NMap is a port scanner you can use for checking all the computers in your LAN for open ports, and it only takes a few minutes to install.
[http://insecure.org/nmap/docs.html](http://insecure.org/nmap/docs.html)
[/COLOR][COLOR=#000000]Nmap is installable in Ubuntu through apt-get, Add/Remove Programs or Synaptic Package Manager.
A nice GUI front end is available for NMap too, it's called '[NmapFE]("http://insecure.org/nmap/SoC/NmapFE.html")', and is available through Add/Remove Applications, and probably apt-get and Synaptic too.

Now that you know what ports your rogue program is opening, you can use Firewall or whatever IP tables front-end you like to close those ports.
[/COLOR][COLOR=#000000][Howto: Setup a Software Firewall in Linux using Firestarter]("http://www.techthrob.com/tech/firestarter.php") - Techthrob.com
[/COLOR][COLOR=#000000]
[/COLOR]If you are still feeling insecure, and you want to keep an eye on all the traffic in your LAN to make sure no rogue programs are doing something bad, you can use Wireshark[COLOR=#000000] - [http://www.wireshark.org/](http://www.wireshark.org/)[/COLOR]
[COLOR=#000000]Wireshark is installable in Ubuntu through apt-get, Add/Remove Programs or Synaptic Package Manager. Wireshark is a packet sniffer, you can use that to keep a watchful eye on the comings and goings of all the packets in your LAN.

[/COLOR][COLOR=#000000] [/COLOR]

---

### Post by Herman on 2008-09-14
> Or is there a way to make another user and disable ALL internet access for that user? I'm trying to run a program and I do NOT want to give it internet access. Actually several programs.Sure, simple!
Just go 'System'-->'Administration'-->'Users and Groups', and you can add a new user in there. You can set the new user's privileges in 'Properties'. :)

---

### Post by solarwind on 2008-09-14
> **Herman said:**
> Sure, simple!
Just go 'System'-->'Administration'-->'Users and Groups', and you can add a new user in there. You can set the new user's privileges in 'Properties'. :)

Awesome. I think that's all I need. I'll also check out apparmor and scan for ports though. Thanks everyone!

---

### Post by Malac on 2008-09-15
You could give this a try:
[http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)
Still pre-release but you could test it.

Hope this helps.

---

### Post by OmegaBLK on 2008-09-15
There is an iptable rule that may enable one to implement some of the functionality of the application filtering capabilities that Personal Firewalls apps in Windows do.   You can probably accomplish this using "--cmd-owner" which is in the "owner" module for iptables.  I have never tried it and may not really do the job well or at all if it is even supported on your particular installation.  Check the iptables manpage for more info on this.  It is still not really comparable to the application filtering that the Personal Firewalls do in Windows, so Apparmor would be the better recommendation to prevent an app that you need to use, but do not want it to connect to the Internet.  If the app uses a specific port you could setup a firewall rule to block that port also.

The closest app I have seen that is similar to what you want:

[Program Guard](http://pgrd.sourceforge.net/) However, it doesn't appear to have been updated in three years though.

---

### Post by OmegaBLK on 2008-09-15
Also check these out:

[L7-filter](http://l7-filter.sourceforge.net/)
[nufw](http://www.nufw.org/)

---

### Post by Herman on 2008-09-15
:) Another strategy, (a very simple solution), that some people might like is to just install more than one Ubuntu. Since Ubuntu is free, we can install as many instance of it as we like, sometimes it's easy to forget that. 
A person could have  a 'file sharing' Ubuntu installation and a 'secure' Ubuntu installation and boot into whichever one they need at the time.

Ubuntu comes with [seahorse]("http://www.gnome.org/projects/seahorse/"), so we can encrypt sensitive files, and send and receive encrypted email. [Set up Seahorse]("http://users.bigpond.net.au/hermanzone/p5.htm#Install_Seahorse") 

If you use the 'Alternate' CD to install Ubuntu with, it's possible to install Ubuntu in an encrypted file system for better security.

---

