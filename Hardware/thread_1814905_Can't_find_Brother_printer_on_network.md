---
title: "Can't find Brother printer on network"
date: 2011-07-30
forum: Hardware
---

### Post by Ameet on 2011-07-30
I had it all set up: Brother HL-5370DW laser printer, connected via ethernet to our router, and my Dell Inspiron 1525, running Ubuntu 11.04 32-bit, also connected to the same router.

It worked fine, until the printer began to give an error sheet when I tried printing a document: 
```

ERROR NAME;
    undefined
COMMAND;
    Q
OPERAND STACK;

```So, I unplugged the printer, and replugged it.  I then deleted the printer from the device list on my Ubuntu Printer panel, and attempted to add it back in. Thought I'd "freshen everything up".

Well, now I can't find the printer on the network!!
[ATTACH]198848[/ATTACH]
I entered the IP address for the router (192.168.1.1).  When I use my browser to access the router, it lists an ethernet device which I believe is the printer, at 192.168.1.45.  If I enter that number, the "New Printer" dialog still can't find my Brother printer.

Also - I couldn't access the CUPS server using the web browser, as I read about elsewhere.  At [http://localhost:631](http://localhost:631).  So I stopped and restarted CUPS (the printer server in Ubuntu), thinking that might help:
```
sudo stop cups
sudo start cups
```
That still doesn't let me access the CUPS server.

It's been a few months since I set the printer up and now I don't remember how I got it going the first time.  What am I doing wrong at this step of the dialog box??

I don't think this is about drivers - this is about how to even recognize the existence of the printer on the network.

Any ideas??

---

### Post by scorchgeek on 2011-07-30
Starting with the stupidest possibility first, make sure the printer you're trying to find is on (I'm assuming you checked that, but just in case....)

Secondly, are you sure 192.168.1.45 is the printer? Try going to that IP address in your browser; on my printer (I have a similar model), I get a web configuration page for the printer. You could also just try all the other IP addresses on your network and see if one is the printer:
```
nmap -sP 192.168.1.1/24
``` should show you the IP addresses of all the devices connected to your network.

---

### Post by Ameet on 2011-07-30
> **scorchgeek said:**
> Starting with the stupidest possibility first, make sure the printer you're trying to find is on (I'm assuming you checked that, but just in case....)

Secondly, are you sure 192.168.1.45 is the printer? Try going to that IP address in your browser; on my printer (I have a similar model), I get a web configuration page for the printer. You could also just try all the other IP addresses on your network and see if one is the printer:
```
nmap -sP 192.168.1.1/24
``` should show you the IP addresses of all the devices connected to your network.

Thanks, scorchgeek.  Let's see, when I go to my router address on my browser, it scans for everything connected to the local network. It shows two ethernet connections - one is my PC at *.24, and the other is definitely the Brother printer, at *.45. It calls the name of the computer at 192.168.1.45 "BRN001BA93C03E9" (which I'm pretty sure is the Brother printer), but -- here's the thing, for Connection Type, it shows "Ethernet" with a red "X" next to it.

When I point my browser to that IP address, I get the error message "Firefox can't establish a connection to the server at 192.168.1.45."

Also, nmap doesn't register the printer:
```
$ nmap -sP 192.168.1.1/24

Starting Nmap 5.21 ( http://nmap.org ) at 2011-07-30 16:12 EDT
Nmap scan report for dslrouter (192.168.1.1)
Host is up (0.0012s latency).
Nmap scan report for 192.168.1.24
Host is up (0.0012s latency).
Nmap scan report for 192.168.1.34
Host is up (0.00100s latency).
Nmap done: 256 IP addresses (3 hosts up) scanned in 2.77 seconds

```(*.34 is my PC's wireless link to the router.)

So, here's what I know:
1) The printer is on. :-)
2) It is physically connected to the router, and the router light reflects that there is a cable connected to that port.
3) The router server remembers the presence of the printer at *.45 but does not show an active software link with it at this time.
4) I cannot find the printer server from my browser (at it's previous IP #).
4) nmap does not find it on the network.
Conclusion: the printer is not doing its job as a network client.  Does this sound right?? Is there any other diagnostic information that would help here??

BTW, is it significant that I can't access the CUPS driver at localhost:631? Is this part of the problem or a different issue?

Thanks for any help!!

---

### Post by scorchgeek on 2011-07-30
Your conclusion seems right to me. You might try powering off the router and the printer, waiting 45 seconds or so, and then switching on the router and then the printer.

Also, what do you mean by 
> (*.34 is my PC's wireless link to the router.)?

I unfortunately don't know why you can't access the CUPS server, nor whether that might have any effect. You might try restarting your computer and trying again, though it's unlikely to help.

---

### Post by Ameet on 2011-07-31
OK. I restarted the computer; then powered off the modem and printer, then powered on the modem, and reset the printer

(How to factory reset the Brother HL-5370DW: [http://welcome.solutions.brother.com/BSC/public/us/us/en/faq/faq/000000/000100/000005/faq000105_007.html?reg=us&c=us&#10216;=en&#8719;=hl5370dw_us]("http://welcome.solutions.brother.com/BSC/public/us/us/en/faq/faq/000000/000100/000005/faq000105_007.html?reg=us&c=us&lang=en&prod=hl5370dw_us") )

Now I can see the printer on my LAN. It is at *.46 (192.1.1.46).

I can point my browser to that IP number and see the printer's web server.  So, thanks for that!

AND - I am able to enter it as a new printer and print a test page successfully. So, so far it looks like the problem is solved.  Thanks, scorchgeek!  :KS

---

### Post by scorchgeek on 2011-07-31
Sorry to reply to a solved thread, but completely out of curiosity, are you now able to access the CUPS server?

---

### Post by brylie on 2011-10-29
I am not sure that this thread is actually solved. The original message was related to an error message.

```
ERROR NAME;
  undefined
COMMAND;
  Q
OPERAND STACK;
```

I have a brother DCP-8080DN and get the previous error when printing from Firefox. I can successfully print from other applications including OO.o, Evince, etc. I think that this is related to the Cairo rendering engine that Firefox uses, but I am uncertain.

What steps can I take to diagnose this issue?

---

### Post by mörgæs on 2011-10-29
Hi, welcome to the fora.

If it concerns Firefox, this thread is a good place to begin:
[http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247)

Thread moved to Hardware and Laptops, by the way.

---

