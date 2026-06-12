---
title: "network printer bricked(?) by win xp in virtualbox"
date: 2012-04-28
forum: Hardware
---

### Post by sudodus on 2012-04-28
I have been happily running a Brother HL-2250DN printer attached via wired ethernet (and Ubuntu 10.04 LTS). But I wanted to print an official pdf document, where I had filled in content, and I needed adobe acrobat, so I tried to install the printer driver from Brother's CD running Windows XP in VirtualBox. That was a bad idea! I should have used xournal instead.

Somehow the printer was assigned the IP address 10.0.2.48, but Windows could not print. And worse, the host system Ubuntu cannot print either. My LAN is managed by an old Netgear router, that wants attached units in the IP address range 192.168.0.2-51. Sometimes(?!) the router can see the printer at 10.0.2.48, but ping gets no response and I just don't know how to get it working again.

I have done the exercise with the 'Go' button to reset the printer to factory settings, I have tried using two other routers (D-Link), but no luck. I have tried arp (but I don't really understand what I am doing). When running the internal test to print the settings, it states

IP Address  10.0.2.48 (set manually)

but I would rather say 'set automatically when installing the printer driver in XP in VirtualBox'.

Fortunately I can print via the USB port, but I lose the flexible access from several computers via the LAN.
     -o-
If you understand more about this than I do, what do you suggest?

- Is there some way to reach the printer, either to continue using the new IP address, or to reset it? Is there some kind of firewall protection, or do I need to use another and more flexible router, or DHCP server (for example Ubuntu)? How can I do that?

- Or should I consider the ethernet port as bricked, and be happy as long as the USB port is working?

---

### Post by ahallubuntu on 2012-04-28
Yes, there should be something on that Brother CD you can run to configure the network settings again.  I'm not sure if you can run it from Virtualbox XP or not, though...


You could start by resetting the printer to factory settings:

[http://welcome.solutions.brother.com/BSC/public/eu/eu_ot/en/faq/faq/000000/000100/000005/faq000105_016.html?reg=eu&c=eu_ot&lang=en&prod=hl2250dn_eu_as&Cat=108](http://welcome.solutions.brother.com/BSC/public/eu/eu_ot/en/faq/faq/000000/000100/000005/faq000105_016.html?reg=eu&c=eu_ot&lang=en&prod=hl2250dn_eu_as&Cat=108)

and then hope that it will again automatically get a new IP from the router via DHCP.  FYI, it's best to use the router to reserve an IP for it (based on the MAC address of the Brother's ethernet card) so it always gets the same IP each time you plug it in, even after you reset the power on the router.  Otherwise, it may have a different IP next time you use it and you won't be able to print to it.  Most routers have the ability to reserve an IP like that.

After you've done this, you can probably delete the printer in Virtual XP and try re-installing it without the CD - just tell Windows to detect it via the IP it now has assigned (hopefully that IP will never change if you do the above) and it should already have the driver installed...

---

### Post by sudodus on 2012-04-29
.

---

### Post by sudodus on 2012-04-29
Thanks for trying to help :-)
> **ahallubuntu said:**
> Yes, there should be something on that Brother CD you can run to configure the network settings again.  I'm not sure if you can run it from Virtualbox XP or not, though...

You could start by resetting the printer to factory settings:

[http://welcome.solutions.brother.com/BSC/public/eu/eu_ot/en/faq/faq/000000/000100/000005/faq000105_016.html?reg=eu&c=eu_ot&lang=en&prod=hl2250dn_eu_as&Cat=108](http://welcome.solutions.brother.com/BSC/public/eu/eu_ot/en/faq/faq/000000/000100/000005/faq000105_016.html?reg=eu&c=eu_ot&lang=en&prod=hl2250dn_eu_as&Cat=108)

and then hope that it will again automatically get a new IP from the router via DHCP.

I have already run that resetting method twice. No luck.
> 
FYI, it's best to use the router to reserve an IP for it (based on the MAC address of the Brother's ethernet card) so it always gets the same IP each time you plug it in, even after you reset the power on the router.  Otherwise, it may have a different IP next time you use it and you won't be able to print to it.  Most routers have the ability to reserve an IP like that.

Yes, this is what I was using. The Brother printer was assigned the address '7', 192.168.0.7, until the unfortunate event with xp in virtualbox. So my router assignment was overridden! I have tried several restarts with and without that assignment in the router setting.

Also, I have tried to re-configure it from Windows XP installed directly (dual boot) from another computer. But it cannot find the printer in the network. (It finds it via USB, but not via ethernet.)
> 
After you've done this, you can probably delete the printer in Virtual XP and try re-installing it without the CD - just tell Windows to detect it via the IP it now has assigned (hopefully that IP will never change if you do the above) and it should already have the driver installed...
I will try again from XP in Virtualbox to delete it, but as I wrote, I had tried, and could not reach it. Can you suggest a command to run from Windows or some powerful command from Ubuntu, maybe some general linux network command.

Still hoping ...

---

### Post by WasMeHere on 2012-04-29
Since you can still use the printer via the USB port, have you considered installing new firmware (or reinstalling the current version of the firmware)? And then, try to manage the printer from Windows via one of the other routers that you tried...

---

### Post by sudodus on 2012-04-29
I could install new firmware via USB, but the problem is the same. I'll do some more testing without my main computer and with another router.

---

### Post by sudodus on 2012-05-07
Is there any LAN expert around here, who might have a clue how to make a printer work again via ethernet?

---

### Post by mips on 2012-05-07
> **sudodus said:**
> Is there any LAN expert around here, who might have a clue how to make a printer work again via ethernet?

> Somehow the printer was assigned the IP address 10.0.2.48, but Windows could not print. And worse, the host system Ubuntu cannot print either. My LAN is managed by an old Netgear router, that wants attached units in the IP address range 192.168.0.2-51. Sometimes(?!) the router can see the printer at 10.0.2.48, but ping gets no response and I just don't know how to get it working again.

1. What is the IP address of your Ubuntu 10.04 LTS PC (post the output of terminal command **ifconfig -a**)
2. What is the IP address of your other PC's ((post the output of terminal command **ifconfig -a** or **ipconfig /all** for windows PCs)
2. What is the IP address of your WinXp virtual setup ((post the output of terminal command **ipconfig /all**)
4. What is the IP address of your router? (See routers web interface, also give me a screenshot of the DHCP config page)

I have a suspicion as to what is going on and it's related to your WinXP guest being natted into to the 10 address range.

You need to configure you printer with a a IP address from the 192.168.0.x address range, you should be able to this from it's control panel. Point the WinXP printer configuration to this IP address.

Alternatively install a PDF print driver in WinXP and print to the PDF driver which will create another PDF file which you can then print from linux. [http://www.techsupportalert.com/best-free-pdf-writer.htm](http://www.techsupportalert.com/best-free-pdf-writer.htm)

---

### Post by sudodus on 2012-05-07
> **mips said:**
> 1. What is the IP address of your Ubuntu 10.04 LTS PC (post the output of terminal command **ifconfig -a**)
2. What is the IP address of your other PC's ((post the output of terminal command **ifconfig -a** or **ipconfig /all** for windows PCs)
2. What is the IP address of your WinXp virtual setup ((post the output of terminal command **ipconfig /all**)
4. What is the IP address of your router? (See routers web interface, also give me a screenshot of the DHCP config page)

I have a suspicion as to what is going on and it's related to your WinXP guest being natted into to the 10 address range.

You need to configure you printer with a a IP address from the 192.168.0.x address range, you should be able to this from it's control panel. Point the WinXP printer configuration to this IP address.

Alternatively install a PDF print driver in WinXP and print to the PDF driver which will create another PDF file which you can then print from linux. [http://www.techsupportalert.com/best-free-pdf-writer.htm](http://www.techsupportalert.com/best-free-pdf-writer.htm)

Is there any security risk posting such info? Would it be OK if I send it in a message to you?

[I]Edit:
1. I have sent such a message now
2. The only control panel I know is via ethernet. There is a button to press (at boot and six times) in order to reset the printer, and I have done that procedure twice. (I think it worked, but it has not fixed the problem.)
3. Yes, there are several alternatives to print those pdf files without installing the printer via the vbox. If we succeed with this task, I will keep my fingers away from any attempts to install the printer via the vbox.
[/I]

---

### Post by mips on 2012-05-07
> **sudodus said:**
> Is there any security risk posting such info? Would it be OK if I send it in a message to you?

No. I just reviewed what you sent me via PM and all the IP addresses in there are private addresses you can't access from the internet. Everybody with a home LAN in the world uses the same address ranges so you are safe to post the info here.
There is no public IP info in anything you sent me so you are safe.

You can however cut the part starting with "Värddatornamn" and ending at "Söklista för DNS-suffix" in the ipconfig /all output for the WinXP vm you gave me if you deem that info to be private to you.

Ok, back to your problem. Your printer has a incorrect IP address, reassign it a IP address in the 192.168.0.x range and edit your /etc/hosts to reverse whatever you did.

```
192.168.0.7	BRN001BA9712324
#10.0.2.48	BRN001BA9712324
```

Go into XP and uninstall the driver and settings for the printer, I'm not sure how brother works but it might just reconfigure it every time you start xp. shut down xp and then rest the printer to default settings so it gets a IP from DHCP, next edit your etc/hosts file and comment out the 10. address. you should be able to rpint from linux now. 

If you have to instal the driver in XP make sure you point it to the 192 address and don't let it configure it for a 10. address. It tires to configure it with a 10. address because it sees it as directly connected to the 10. LAN winxp sits in and does not realise it's natted.

---

### Post by sudodus on 2012-05-07
Thank you mips!

I will try what you suggested and report the result.

---

### Post by sudodus on 2012-05-07
> **mips said:**
> ...

Ok, back to your problem. Your printer has a incorrect IP address, reassign it a IP address in the 192.168.0.x range and edit your /etc/hosts to reverse whatever you did.

```
192.168.0.7	BRN001BA9712324
#10.0.2.48	BRN001BA9712324
```
Done> 
Go into XP and uninstall the driver and settings for the printer, I'm not sure how brother works but it might just reconfigure it every time you start xp.

shut down xp and then rest the printer to default settings so it gets a IP from DHCP,This was already done when I started the thread>  next edit your etc/hosts file and comment out the 10. address. you should be able to rpint from linux now. 

If you have to instal the driver in XP make sure you point it to the 192 address and don't let it configure it for a 10. address. It tires to configure it with a 10. address because it sees it as directly connected to the 10. LAN winxp sits in and does not realise it's natted.
I'll start testing ...

---

### Post by sudodus on 2012-05-08
I have uninstalled the Brother printer driver from winxp in vbox (long ago, and I checked it last night: nothing found). I have changed /etc/hosts in Ubuntu 10.04, changed the reserved IP table in the router and restarted the whole environment: router, printer, computer(s). Finally a made a new attempt(?) to reset the printer.

I made a complete poweroff for several minutes. Vbox is not started. Still somewhere there is a trace left, so that the printer thinks it has the IP adress 10.0.2.48, as seen by the router, but it is not responsive in the network.

Could the bad IP address be stored in the printer's ethernet interface? Or am I overlooking something?

*Edit*: now, after about 50 minutes (without reboot), the router is not seeing anything at 10.0.2.48, it does not see the printer at all. It is not responding to ping, neither at
192.168.0.7 nor 10.0.2.48

```
$ ping BRN001BA9712324
PING BRN001BA9712324 (192.168.0.7) 56(84) bytes of data.
From April-2008 (192.168.0.2) icmp_seq=1 Destination Host Unreachable
...
^C
--- BRN001BA9712324 ping statistics ---
10 packets transmitted, 0 received, +9 errors, 100% packet loss, time 9048ms

$ ping 10.0.2.48
PING 10.0.2.48 (10.0.2.48) 56(84) bytes of data.
^C
--- 10.0.2.48 ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 9072ms
```

---

### Post by mips on 2012-05-08
Yes the IP can be stored if the windows gui installer configured it.

Press **Go** three times within 2 seconds to print network settings information.


From the Brother network manual:

```
**Reset the network settings to the factory default**

You can reset the print server back to its default factory 
settings (resetting all information such as the password 
and IP address information). 

a. Turn off the machine.
b. Make sure that the front cover is closed and the
   power cord is plugged in.
c. Hold down **Go** as you turn on the power switch. Keep
   **Go** pressed down until all the LEDs light up and then
   **Ready** LED turns off.
d. Release **Go**. Make sure that all the LEDs turn off.
e. Press **Go** six times. Make sure that all the LEDs light
   up to indicate the print server has been reset to its
   factory default settings. The machine will restart.
```

After you have done this wait 2 minutes or so and then print another settings page.

---

### Post by sudodus on 2012-05-08
> **mips said:**
> Yes the IP can be stored if the windows gui installer configured it.

If you print a test page by pressing the go button on the printer does it give you any config info on that test page?

From the Brother network manual:
Yes, it has stated for a long time (when printing the printer settings)
...
IP Address   10.0.2.48  (set manually)
subnet mask  255.255.255.0
IP Gateway   192.168.0.1
Boot method  STATIC
...

And this is although I have used the method you quoted (pressing the button and looking at the LEDs) several times, also today. There is one thing, that might screw things up: I have a warning, that the toner is low. It is still printing very well (via USB), but maybe that warning status prevents complete resetting.

*Edit: the printer settings output shows graphically, that there should be ~40% left of the toner, so it is not very low.*

---

### Post by mips on 2012-05-08
> **sudodus said:**
> Yes, it has stated for a long time (when printing the printer settings)
...
IP Address   10.0.2.48  (set manually)
subnet mask  255.255.255.0
IP Gateway   192.168.0.1
Boot method  STATIC
...

**And this is although I have used the method you quoted (pressing the button and looking at the LEDs) several times, also today. **

You sure you are doing it right?

If the reset procedure does not work then:

a. directly connect a pc to the printer via a crossover ethernet cable. Configure the pc with a 10.0.2.50 ip address and try and access it via it's web interface to reset.

b. reconfigure your entire network, pc & router to the 10.0.2.0 network and try and connect to it via it's web interface.

---

### Post by sudodus on 2012-05-08
> **mips said:**
> You sure you are doing it right?
 No, I'd be crazy to be 100% sure :P> 
If the reset procedure does not work then:

a. directly connect a pc to the printer via a crossover ethernet cable. Configure the pc with a 10.0.2.50 ip address and try and access it via it's web interface to reset.

I have an ethernet crossover cable somewhere. How do I configure the PC's IP address in this case?

And would it be hard to reverse, in other words, should I do it booted from a live Ubuntu USB drive? Would it be easier to do it from a PC with WinXP installed (direct install, no vbox)? Suggest whatever is easy for you to guide ;-)
> 
b. reconfigure your entire network, pc & router to the 10.0.2.0 network and try and connect to it via it's web interface.
This would be the last option.

---

### Post by mips on 2012-05-08
> **sudodus said:**
> No, I'd be crazy to be 100% sure :P
I have an ethernet crossover cable somewhere. How do I configure the PC's IP address in this case?

And would it be hard to reverse, in other words, should I do it booted from a live Ubuntu USB drive? Would it be easier to do it from a PC with WinXP installed (direct install, no vbox)? Suggest whatever is easy for you to guide ;-)


Yeah, boot with a livecd if you don't wanna make any changes.
Configure your IP address manually:
IP- 10.0.2.10
Netmask- 255.255.255.0
You don't need to configure a gateway but if you must just use 10.0.2.1 not that it will be useful for anything.
See if you can ping the printer.

If you still have no luck then try a XP machine connected to it with the brither configuration utility. XP machine will use the same IP details as above.

If you wanna livechat at any stage during this join me on IRC, irc.freenode.net, #mips1911 might be faster than going backwards and forwards here.


> **sudodus said:**
> 
This would be the last option.

That I would agree with :biggrin:

---

### Post by sudodus on 2012-05-08
Supported by you, *mips*, as well as the following link, I set up a crossover network with my IBM T41 laptop with Lubuntu 12.04 live, and when I ping to 10.0.2.48 I get response and no packet loss :-) I guess the next step is to try to log in to the printer10.0.2.48 via the network.

[[COLOR="Red"]_http://www.linuxquestions.org/questions/linux-networking-3/file-transfer-using-ethernet-cross-over-cable-802756/_[/COLOR]]("http://www.linuxquestions.org/questions/linux-networking-3/file-transfer-using-ethernet-cross-over-cable-802756/")
or more specifically this reply

> SUCCESS! Thanks everyone!
[QUOTE]
[Originally Posted by damgar]
In your set up you will have 2 servers. Any machine sharing it's resources is a server.

Set an IP on each computer's ethernet port, if there's only one than that is eth0, to be in the same subnet. Like :

```
desktop
IP address 192.168.1.5
subnet mask 255.255.255.0
gateway 192.168.1.6

laptop
IP address 192.168.1.6
subnet mask 255.255.255.0
gateway 192.168.1.5

```
The gateways may not even be neccessary, but can't hurt. You'll have to make sure that they are in the same workgroup, at my house I call it "workgroup" because I'm lazy and it's easy.

The IP addresses can be set in NetworkManager (the little computer icons on the panel)if you don't see it, use the "add to panel" feature to enable it.

Then in places go to network and if it doesn't see the other machine try clicking on "windows network" or something to that effect, use context clues.

Post back if you can't get it from there.
I setup the system as you suggested and it works fine. It is exactly what I was looking for. Thanks for everyones help.[/QUOTE]

---

### Post by mips on 2012-05-08
> **sudodus said:**
> I guess the next step is to try to log in to the printer10.0.2.48 via the network.


Open a web browser and use this url to connect to it, [http://10.0.2.48/](http://10.0.2.48/)

Default login details are,
User: admin
Password: access

You can now change the IP details to match your 192.168.0.x network and save it.

---

### Post by sudodus on 2012-05-08
The next step was successful. I logged into the printer's web user interface, and I changed the default IP address to the one I want, 192.168.0.7

```
$ fpinga
quick list without numbers
Netgear-Router
April-2008
BRN001BA9712324
slow list with numbers, quit by ctrl C twice
1  Netgear-Router is alive
2  April-2008 is alive
3  Jan-2004 is unreachable
4  xw8400 is unreachable
5  tc-2 is unreachable
6  NI-2010 is unreachable
7  BRN001BA9712324 is alive
$
```
Now I get response from the printer in my standard network, and I can log into it again via ```
firefox 192.168.0.7
``` :-)

Obviously the resetting was not successful, even my custom made password had survived. Maybe the resetting only affects the standard printer settings(?!), or the 'toner low' message garbled the reset procedure.

You have guided me to a solution. Thank you very much, *mips* :KS

---

### Post by mips on 2012-05-08
> **sudodus said:**
> 
Obviously the resetting was not successful, even my custom made password had survived. Maybe the resetting only affects the standard printer settings(?!), or the 'toner low' message garbled the reset procedure.

You have guided me to a solution. Thank you very much, *mips* :KS

Glad I could help.

That reset procedure is suppose to reset the printers built in print server IP config to factory defaults (as well as the normal printer settings).

---

### Post by sudodus on 2012-05-08
When I could reach the network interface, I knew the problems would be solved. But anyway, now I can confirm writing via ethernet from two computers, so the printer is back in business again :-)

---

### Post by Justin Baskaran on 2012-08-21
i got an error like this on my brother hl 220dw

---

