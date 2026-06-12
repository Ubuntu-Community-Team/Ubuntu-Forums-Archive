---
title: "Remote Assistance like Windows"
date: 2008-09-06
forum: General Help
---

### Post by fballem on 2008-09-06
When I was working in New York, I was able to support my Toronto clients remotely. All of the systems were using Windows. There were two ways: we could use Windows Messenger, in which case they could request Remote Assistance, or through Windows (Vista) where they could request Remote Assistance. Either way, I could connect to their computer and view what they were doing, or even take control.

I've just converted one of my clients to ubuntu, and I'm running ubuntu. Is there a way of doing the same thing as I used to be able to do? We are in different physical buildings, and totally separate networks.

Thanks,

---

### Post by hyper_ch on 2008-09-06
have a look at "vnc"

---

### Post by The Cog on 2008-09-06
Ask your client to go System->Preferences->Remote Desktop and allow other users to view and control.

---

### Post by fballem on 2008-09-06
> **The Cog said:**
> Ask your client to go System->Preferences->Remote Desktop and allow other users to view and control.

That sounds intriguing. Two questions:
[LIST=1]
[*]Does it matter that we're not on the same network?
[*]What do I have to do in order to connect once she gives me permission?
[/LIST]

Thanks,

---

### Post by callan79 on 2008-09-06
> **fballem said:**
> 
[*]Does it matter that we're not on the same network?
[*]What do I have to do in order to connect once she gives me permission?



Hi fballem,

I do a fair bit of remote-access support, so here's a quick summary. Note that VNC is availale for Ubuntu and Windows, so I'll include notes for each.

NB - VNC for Windows is at [http://www.realvnc.com](http://www.realvnc.com)


(1) On the target machine, make sure VNC Server is running. On Windows, this means fire it up from the Start Menu (or choose to run as a service when you install it). On Ubuntu, System >> Preferences >> Remote Desktop and make sure "allow other users..." and "allow users to control..." are selected. Recommend "ask for confirmation" NOT ticked, but "ask for password" IS ticked, and a secure password typed in. There are similar settings in VNC for Windows too.

(2) On your machine, start your VNC Viewer. On Ubuntu, this is Applications >> Internet >> Remote Desktop Viewer. On Windows, it's the VNC Viewer on your Start Menu.

(3) Type in the target machine's IP Address and click connect.


Now, Step (3) is the hardest one, as these days most people use Broadband and are behind some type of firewall our router.

This means you need to type in their Internet IP, and you might need to set up a port forwarding for VNC Port 5900 to the actual computer.

Does this make sense so far?

If you need more details about Step 3 just ask!

Cheers
Callan

---

### Post by fballem on 2008-09-06
> **callan79 said:**
> Hi fballem,

I do a fair bit of remote-access support, so here's a quick summary. Note that VNC is availale for Ubuntu and Windows, so I'll include notes for each.

NB - VNC for Windows is at [http://www.realvnc.com](http://www.realvnc.com)


(1) On the target machine, make sure VNC Server is running. On Windows, this means fire it up from the Start Menu (or choose to run as a service when you install it). On Ubuntu, System >> Preferences >> Remote Desktop and make sure "allow other users..." and "allow users to control..." are selected. Recommend "ask for confirmation" NOT ticked, but "ask for password" IS ticked, and a secure password typed in. There are similar settings in VNC for Windows too.

(2) On your machine, start your VNC Viewer. On Ubuntu, this is Applications >> Internet >> Remote Desktop Viewer. On Windows, it's the VNC Viewer on your Start Menu.

(3) Type in the target machine's IP Address and click connect.


Now, Step (3) is the hardest one, as these days most people use Broadband and are behind some type of firewall our router.

This means you need to type in their Internet IP, and you might need to set up a port forwarding for VNC Port 5900 to the actual computer.

Does this make sense so far?

If you need more details about Step 3 just ask!

Cheers
Callan

If it makes it easier, both machines are ubuntu. First of all, how do I get the IP address for their machine (we both use dynamic IPs from different providers). Secondly, how do I do the port forwarding thing that you're speaking of?

Many thanks,

---

### Post by The Cog on 2008-09-07
This web site will gove you your current IP address:
[http://whatismyipaddress.com/](http://whatismyipaddress.com/)

You will need to arrange for the router in front of the PC receiving the connection to pass the connection on to the PC. VNC uses TCP port 5900. 

Don't let your client leave remote desktop enabled, even password protected, because there are bots out there looking for VNC servers.

You may prefer to only allow SSH through the firewall/router, and then tunnel the VNC through SSH. This is probably more secure, and also permits using SSH to do file transfer if needed.

---

### Post by lost_soul on 2008-09-08
Do the guy you installed ubuntu for have Real IP in the first place? or is he supplied by a fake IP from his ISP if thats the case you can not connect to him remotly ..

---

### Post by fballem on 2008-09-08
> **lost_soul said:**
> Do the guy you installed ubuntu for have Real IP in the first place? or is he supplied by a fake IP from his ISP if thats the case you can not connect to him remotly ..

a 'fake IP address' from the ISP. If I cannot connect to her, then I would wonder how Windows is able to do it, since the only thing that I've changed in the setup is replacing Windows with ubuntu on both systems.

---

### Post by callan79 on 2008-09-08
> **fballem said:**
> a 'fake IP address' from the ISP. If I cannot connect to her, then I would wonder how Windows is able to do it, since the only thing that I've changed in the setup is replacing Windows with ubuntu on both systems.


You should be pretty much right with the current setup.

If you're connecting to computers on the same network then you just type in their IP. If you're connecting to computers elsewhere on the 'net, then there are a few things you need to get out the way first.

If you go to [www.whatismyip.com](http://www.whatismyip.com), you can find out the real IP Address of an Internet Connection. YOUR IP does not matter, but you'll need to know the IP which runs the connection of the target machine.

So :

(1) Set your client's computer to a Static IP on their network. So instead of letting their ADSL/Cable router supply 192.168.100.1 or something that might be different with each boot, set it manually so it's always the same.

(2) In your client's modem/router, forward port 5900 to the IP of their computer.

(3) Get your client to allow remote desktop connections, password protected of course, via System >> Preferences >> Remote Desktop.

(4) Get your client to go to [www.whatismyip.com](http://www.whatismyip.com) to find the IP of their Internet Connection.

(5) On your computer, go to Applications >> Internet >> Remote Desktop Viewer, connect to their IP Address, and it should all work.


The above is the 'proper' way to get this done, and in fact the hardest bit is getting all the IPs and Firewalls set up properly in the first place, but once it's done it'll work perfectly without fail, every single time.

If you're stuck on any of the above, just reply and tell us which point you're not sure about and we can explain more.

By the way, it'd be helpful if you could tell us:

 - brand and model of your client's ADSL/Cable Modem/Router
 - is your client's Internet IP and his/her Computer IP the same, or different? To determine Internet IP, to go [www.whatismyip.com](http://www.whatismyip.com). To determine Computer IP right click on the network connection up by the clock, choose connection information. If it starts with a 192.168 or a 10.0 then you can safely tell us here. If it starts with something else then only quote the first set of numbers, not the whole thing (example my Computer's IP is 192.168.7.21, my Internet IP is 202.xxx.xxx.xxx).

Cheers
Callan

---

### Post by fballem on 2008-09-08
> **callan79 said:**
> You should be pretty much right with the current setup.

If you're connecting to computers on the same network then you just type in their IP. If you're connecting to computers elsewhere on the 'net, then there are a few things you need to get out the way first.

If you go to [www.whatismyip.com](http://www.whatismyip.com), you can find out the real IP Address of an Internet Connection. YOUR IP does not matter, but you'll need to know the IP which runs the connection of the target machine.

So :

(1) Set your client's computer to a Static IP on their network. So instead of letting their ADSL/Cable router supply 192.168.100.1 or something that might be different with each boot, set it manually so it's always the same.

(2) In your client's modem/router, forward port 5900 to the IP of their computer.

(3) Get your client to allow remote desktop connections, password protected of course, via System >> Preferences >> Remote Desktop.

(4) Get your client to go to [www.whatismyip.com](http://www.whatismyip.com) to find the IP of their Internet Connection.

(5) On your computer, go to Applications >> Internet >> Remote Desktop Viewer, connect to their IP Address, and it should all work.


The above is the 'proper' way to get this done, and in fact the hardest bit is getting all the IPs and Firewalls set up properly in the first place, but once it's done it'll work perfectly without fail, every single time.

If you're stuck on any of the above, just reply and tell us which point you're not sure about and we can explain more.

By the way, it'd be helpful if you could tell us:

 - brand and model of your client's ADSL/Cable Modem/Router
 - is your client's Internet IP and his/her Computer IP the same, or different? To determine Internet IP, to go [www.whatismyip.com](http://www.whatismyip.com). To determine Computer IP right click on the network connection up by the clock, choose connection information. If it starts with a 192.168 or a 10.0 then you can safely tell us here. If it starts with something else then only quote the first set of numbers, not the whole thing (example my Computer's IP is 192.168.7.21, my Internet IP is 202.xxx.xxx.xxx).

Cheers
Callan

Thanks - I think the router on the client side is supplied by Bell Canada (the local telephone company). I should not have a problem setting her to a static id, but there could be a challenge to reconfigure the router to redirect port 5900. I'll have to check the next time that I go in.

Many thanks and I'll post the results.

---

### Post by sefs on 2008-09-08
If this is a long term solution....


1) grab a domain name from dyndns.org.  Most residential routers support it.  That would solve your IP problems on the client end.

2) Once you have vnc up and running I would then recommend in the long term using OpenSSH and tunnel vnc thru that. Unless vnc now comes with built in encryption of some sort.

---

### Post by ryanhaigh on 2008-09-08
Rather than having to configure port forwarding etc. for all your clients I would look at reverse VNC. With reverse VNC you run a listening VNC viewer on your computer and the client establishes the connection to you. This way you only need port forwarding on your system and if you use dyndns or an equivalent service the client doesn't need to know your IP.

[http://gentoo-wiki.com/VNC#Reverse_VNC](http://gentoo-wiki.com/VNC#Reverse_VNC)

[http://lifehacker.com/software/vnc/tech-support-with-vnc-reverse-connections-250794.php](http://lifehacker.com/software/vnc/tech-support-with-vnc-reverse-connections-250794.php)

OLD instructions: [http://ubuntuforums.org/showthread.php?t=299489](http://ubuntuforums.org/showthread.php?t=299489)

According to the roadmap for Gnome 2.24 Vino (the vnc server associated with System > Preferences > Remote Desktop) will support reverse connections so it will be much easier in the future.

---

