---
title: "ssh into remote kubuntu that is behind dsl router"
date: 2005-11-18
forum: General Help
---

### Post by dragonflyFZX on 2005-11-18
hi,

i want to connect to my laptop at home using a secure shell.  According to the help, just installing the openssh-servers should do.  To connect, it says, just issue the command:

ssh username@computeryouwanttoconnectto

when i do that, nothing hapens.  After some time i get the error: connection timed out.  I think the problem is that i am using a adsl connection (using the popular speedtouch router), because when i take the laptop to may work and connect it to the network i can ssh without any problem.  Can someone explain me in plain english how i manage to get through this router?  I have to warn you that i dont understand a thing about port forwarding, IP, etc.

And oh yes, i dont really know what ip address i have to use in the ssh username@ipaddress command.  If i do a ifconfig, it gives me an ip next to the eth0, but that is different from the one I get using for instance [www.whatismyip.org](www.whatismyip.org)

any help would be greatly appreciated

---

### Post by adwait on 2005-11-18
Well your problem lies in portforwarding. Forward the SSH port (22 or 23 I think....) and you'll be fine. For information on how to do that, check out [www.portforward.com](www.portforward.com)

---

### Post by dragonflyFZX on 2005-11-18
when i do that, i still cant ssh into my machine, i now immediately get:

ssh: connect to host xx.xxx.xxx.xx port 22: Connection refused

:( 

btw, since i can not physically run from one place to the other all the time, i am actually trying to go into my own machine, through ssh, but i can do that on another machine at work that is not behind this router, not from this machine, so i dont think that is the reason why it is not working. I dont know if the port forwarding is the problem.  If i test the port from one of those security websites, they all tell me port 22 is open.  My router on the other hand says not LISTEN, but NONE in that NAPT table...

---

### Post by adrianhensler on 2005-11-18
Hi,

You want to use your whatsmyip.com IP; that is the one that can be reached by the outside world. The IP address that you see from ifconfig (while connected to your router at home) is likley a 192.168.x.x one assigned by your router and won't do you any good from the interent side.

There are these two links:
[http://www.portforward.com/english/routers/port_forwarding/Thomson-Alcatel/SpeedTouch540/SSH.htm](http://www.portforward.com/english/routers/port_forwarding/Thomson-Alcatel/SpeedTouch540/SSH.htm)

and
[http://www.portforward.com/english/routers/port_forwarding/Thomson-Alcatel/SpeedTouch510v4.2/SSH.htm](http://www.portforward.com/english/routers/port_forwarding/Thomson-Alcatel/SpeedTouch510v4.2/SSH.htm)

Check them out and see if they help. One thing I don't know about your setup is if your adsl IP is fairly static or dynamic. If you go to work and your ip has changed by the time you get there; this won't help of course.

Could your work be blocking port 22 perhaps?

ajh

---

### Post by mlomker on 2005-11-18
[QUOTE=adrianhensler]Could your work be blocking port 22 perhaps?
[/QUOTE]

You cannot use NAT or port forwarding in conjunction with SSH--it won't allow it.  SSH is a secure protocol and if it allowed port forwarding then there'd be a million ways to exploit that.  You'll have to either enable telnet instead or (a much more elaborate approach) set up a VPN into the network.

---

### Post by adrianhensler on 2005-11-18
I'm confused - I ssh into my PC all the time using port forwarding. I forward port 22 on the router to port 22 on whichever PC I want at the time. Ssh quite easily traverses NAT; that is one of it's abilities. I send all my MSN and web browsing though it when I am away from home.

---

### Post by Sloth on 2005-11-18
Yes, I ssh in all the time.

You need to make sure the port has been opened in the firewall, and that you are using the external (not internal) IP address.

---

### Post by nrwilk on 2005-11-18
I have a similar question.  What if the computer I want to ssh into is one of multiple computers on a hub.  My situation is like this:

fairly static IP DSL connection -> DSL modem -> 4-port ethernet hub -> the hub goes to 2 Macs and one AMD box, which dual-boots Kubuntu breezy and WinXP.

Say, for example, the internal IP for the Kubuntu box is 192.168.0.2, the hub's IP is 192.168.0.1, and my external IP is 111.222.333.444.  What do I need to do to ssh into the Kubuntu box?

Can I do something like ssh 192.168.0.2@111.222.333.444?

Is there a way to do this?

---

### Post by adrianhensler on 2005-11-18
There are three easy ways.

1. Set up your router for remote access if possible; and configure it that way. I can use the web interface to configure my router and redirect the port 22 to whichever PC I want. But that's not terribly secure; so I turned off the routers remote access:

2. Router allows for local access only; and I ssh into my PC using ssh's socks ability (look for the "ssh -D" options in the man pages or google "ssh proxy"). Now I can (from my desk away from home) browse to [http://192.168.1.1](http://192.168.1.1) and configure my router to now send ssh to whatever PC I want.

3. (My preferred method) Just chain your ssh commands; ssh into one PC and then ssh from that one to the other. There should be no problem stringing these into one command if needed (I just go one at a time; it's usually easier to type and troubleshoot) and while I usually don't need to; you should be able to forward X11 or vnc this way as well.

---

### Post by nrwilk on 2005-11-18
So, I take it that if you ssh into a network like the one I described, you just get automatically forwarded to the first box on the hub?  Would it forward to the first box in ascending IP order, and return a failure error if that box had no ssh capabilities, or would it try IPs until it found a box that had ssh capabilities?

So, my Powermac is first on the hub, and it does have ssh capabilities.  I can ssh to my external IP, and I'd get that box?  Then I'd ssh from that box to the internal IP of the Kubuntu box?

I just like to have a nice grasp of anything I do on my computer, because I'm a geek like that.

Edit: I tried just sshing to my external IP and I get a Connection Refused error.  maybe I didn't understand how to do it?

---

### Post by incubus on 2005-11-18
Fealos,
Are you sure you are using just a plain modem? Isn't it also a router? I have zero experience with Macs, but try to check the IPs your computers have and your external IP, they are probably different.

Then try to find who is "administering" the shared internet connection there. If that's the router, you'll have to read the manual to configure it to forward data from a port to the desired internal IP you got in the first paragraph. If it's one of the Macs, you have to configure there. But from what I know, I don't think the data will be forwarded to the "first computer in the hub".

---

### Post by nrwilk on 2005-11-18
[QUOTE=incubus]Fealos,
Are you sure you are using just a plain modem? Isn't it also a router? I have zero experience with Macs, but try to check the IPs your computers have and your external IP, they are probably different.

Then try to find who is "administering" the shared internet connection there. If that's the router, you'll have to read the manual to configure it to forward data from a port to the desired internal IP you got in the first paragraph. If it's one of the Macs, you have to configure there. But from what I know, I don't think the data will be forwarded to the "first computer in the hub".[/QUOTE]

Macs work the same way as any other computer in this area.  OS X is based on the BSD kernel.  I have a pure DSL modem, which is hooked into an ethernet switch, whose IP is 192.168.0.1.  The computers are 192.168.0.2, ...3, and ...4.  That makes a bit more sense.  The manual for the switch says nothing about port forwarding, or anything along those lines at all.  It's a linksys switch.

---

### Post by adrianhensler on 2005-11-19
Oops. If this is a hub as you say then you can not do any port forwarding. I made a boo-boo and assumed you *meant* router. I'm used to people using terms like switch/hub/router to mean the same thing...

If this is a switch; then you have configured all of your computers manually?  May I ask the model name/number of your switch?

---

### Post by adrianhensler on 2005-11-19
Or; you could reverse ssh tunnel....

Assume you want to ssh into your work PC from your home PC. Your work PC is behind the switch. You should be able to go to your work PC and ssh to your home machine like this:

ssh -R remote_port:localhost:22 your_home_computer

ex. ssh -R 2048:localhost:22 home.computer.com

At home, you would then run ssh -p 2048 localhost to log into your work computer via ssh.

In your example; reverse the situation because I just realized that you want to ssh into your home PC.  There is more info from where I cut this example: 
[http://www.brandonhutchinson.com/ssh_tunnelling.html](http://www.brandonhutchinson.com/ssh_tunnelling.html)

I haven't done this; but it seems fairly straightforward.

---

### Post by nrwilk on 2005-11-19
> **adrianhensler]Or said:**
> http://www.brandonhutchinson.com/ssh_tunnelling.html[/url]

I haven't done this; but it seems fairly straightforward.

So, I've got $ ssh -R 22:192.168.0.2:22 <external IP here>
but I still get a "Connection Refused" error here.  I'm thinking there's some very basic property of ssh that I haven't applied yet that I'm missing.  Do I need the computer's login name and password somewhere in a file or in the command?  I checked to make sure that I have remote logins turned on, and I do.

Also, I checked, and I CAN ssh into the Mac internally.  So, it is working.

Thanks so much for the help, everyone!

---

### Post by dragonflyFZX on 2005-11-19
[QUOTE=adrianhensler]Hi,



Check them out and see if they help. One thing I don't know about your setup is if your adsl IP is fairly static or dynamic. If you go to work and your ip has changed by the time you get there; this won't help of course.

Could your work be blocking port 22 perhaps?

ajh[/QUOTE]

i followed the instructions from the links you gave, not working... Connection refused as said above.  My ip is farily static. Also, i dont thinkt my work is blocking the ports, as they encourage us to use it instead of telnet.  Maybe it has to do something with the ssh settings? Also as said above, the ports seem to be open even without this port forwarding if I use one of these security scanners.

---

### Post by adrianhensler on 2005-11-19
[QUOTE=Fealos]So, I've got $ ssh -R 22:192.168.0.2:22 <external IP here>
but I still get a "Connection Refused" error here.  I'm thinking there's some very basic property of ssh that I haven't applied yet that I'm missing.  Do I need the computer's login name and password somewhere in a file or in the command?  I checked to make sure that I have remote logins turned on, and I do.

Also, I checked, and I CAN ssh into the Mac internally.  So, it is working.

Thanks so much for the help, everyone![/QUOTE]

Hi Fealos; 

If you can ssh either in or out of your 192.168 domain; then you can get a ssh tunnel set up.

If your work domain is IP aa.bb.cc.dd; and your hub (replacing this with a cheap router might make things easier; you could avoid all this messing around with a simple port forward) is blocking ssh from work to home; then what you need to do is ssh the other way; from home to work.

So from home you would

ssh -R 22:localhost:22 aa.bb.cc.dd
(note; use 'localhost'; not 192.168.x.x)

This would take the remote port 22 on your work PC and forward back it to your localhost:22. 
Now when you are at your work PC you can:
ssh localhost
and this should connect using the tunnel. You may need to change from port 22 to something else; 
ssh -R 2200:localhost:22 aa.bb.cc.dd

then from work you would

ssh -p 2200 localhost

Now; this assumes that you can ssh from your home to work. I fyou can't do that; then I think you either need to figure out if your hub/switch has port forwarding or buy a router. You could also just take the switch out of the equation and plug your Mac right into the modem for testing purposes.

Hope this helps? 

(edit - fixed error; I had ssh -2 2200 localhost instead of the correct ssh -p 2200 localhost)

---

### Post by adrianhensler on 2005-11-19
[QUOTE=dragonflyFZX]i followed the instructions from the links you gave, not working... Connection refused as said above.  My ip is farily static. Also, i dont thinkt my work is blocking the ports, as they encourage us to use it instead of telnet.  Maybe it has to do something with the ssh settings? Also as said above, the ports seem to be open even without this port forwarding if I use one of these security scanners.[/QUOTE]

You work may encourage you to use ssh; but do they allow it to leave the network? I don't think it could be a setting for ssh; I'v enever had to change any of the settings to get it to work. 
So if you use the correct ip (not a 192.168.x.x) and try to connect to your laptop at home you get a cennection refused?

And you can ssh into your laptop when you take it to work; so ssh is actually listening for connections.

If you've forwarded port 22 on your rouiter to port 22 on the correct internal (192.168.x.x) IP that should be all you need to do at home.

There must be something else going on here I think.

---

### Post by dragonflyFZX on 2005-11-19
[QUOTE=adrianhensler]
So if you use the correct ip (not a 192.168.x.x) and try to connect to your laptop at home you get a cennection refused?
[/QUOTE]
does it make sense to test this from my laptop at home?  I.e. ssh into my own laptop using the outside ip address?  Caus that does not work...

never mind, my friend just managed to connect to my laptop ! thanx everyone.

---

### Post by mlomker on 2005-11-19
[QUOTE=adrianhensler]I forward port 22 on the router to port 22 on whichever PC I want at the time. [/QUOTE]

I stand corrected, but I thought I had read that somewhere.  I have firewalls with VPN's at home and work and have never needed to test it.

---

### Post by bethnesbitt on 2007-02-11
I need help accepting files through kopete's irc.  Do I need to open a perticular port and if so how?

---

