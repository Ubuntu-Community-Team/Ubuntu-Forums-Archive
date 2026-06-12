---
title: "Modem Problem"
date: 2004-11-22
forum: Hardware &amp; Laptops
---

### Post by jozmak on 2004-11-22
Hi,

I have just installed Ubuntu and I cannot make my modem work. My machine has three operating system, XP, Fedora 2 and Ubuntu. I have an external Robotics modem, which works great with XP and Fedora. In Fedora, you just make a modem link to the ttyS0 port in /dev and you are ready to go. Because I found no information on the ubuntu website on modems I did the same in ubuntu. When I try to activate the connection the modem dials but somehow it never connects. I don’t know what else I can do. 
Any suggestion would be appreciated.

jozmak

---

### Post by az on 2004-11-22
Open a console and try 
sudo pppconfig
then save your information
exit and do
sudo pon

if that works, add the modem lights applet to your panel.  It uses pon and poff.
(poff hangs up)

If that does not work, some people have said that wvdial works for them.  It is in universe.

If that does not work I have no idea.

---

### Post by jozmak on 2004-11-23
Hi AZZ

I tried both of your suggestions. The result was the same. The modem dials, tries to connect then nothing. 
When I run the wvdial utility I found the following criptic output in the consol. I copied it here, maybe it can help to identify the problem.

root@ubuntu:/home/mak # wvdial
--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0L3
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0L3
OK
--> Modem initialized.
--> Sending: ATDT5144489294
--> Waiting for carrier.
ATDT5144489294
CONNECT 44000/ARQ/V90/LAPM/V42BIS
--> Carrier detected.  Waiting for prompt.
** Ascend Pipeline Terminal Server **
ascend%
--> Hmm... a prompt.  Sending "ppp".
ppp
    PPP: Not enabled
ascend%
--> Hmm... a prompt.  Sending "ppp".
ppp
    PPP: Not enabled
ascend%
--> Hmm... a prompt.  Sending "ppp".
ppp
    PPP: Not enabled
ascend%
--> Hmm... a prompt.  Sending "ppp".
ppp
    PPP: Not enabled
ascend%
--> Hmm... a prompt.  Sending "ppp".
ppp
    PPP: Not enabled
ascend%
--> Don't know what to do!  Starting pppd and hoping for the best.
--> Starting pppd at Mon Nov 22 19:08:21 2004
--> pid of pppd: 5081
--> Using interface ppp0
--> pppd: +FCLASS=0L3
--> pppd: +FCLASS=0L3
--> pppd: +FCLASS=0L3
--> pppd: +FCLASS=0L3
--> pppd: +FCLASS=0L3
--> pppd: +FCLASS=0L3
--> Disconnecting at Mon Nov 22 19:08:52 2004
--> The PPP daemon has died: PPP negotiation failed (exit code = 10)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 10)

jozmak

---

### Post by zenwhen on 2004-11-23
Give gnome-ppp a try. It makes configuring dialup in Linux a snap.

---

### Post by mr_ed on 2004-11-23
Did you do sudo pon?  Or did you type in sudo pon <name-of-connection-that-you-called-it-in-pppconfig>?

---

### Post by az on 2004-11-23
We seem to have the same areacode.  What is your isp?  It is sending you a wierd prompt...

---

### Post by jozmak on 2004-11-23
I downloaded gnome-ppp but some xml parser module is missing from ubuntu and I couldn&#8217;t compile the program. And I cannot download the module because I don&#8217;t have connection. 
I tried pon too. It starts dialing, tries to connect then the connection dies. 
[http://295.ca](http://295.ca) this is the isp. I am with them a bit less than a year and so far no complain. Both XP and Fedora works well with this isp.

---

### Post by az on 2004-11-23
There are different ways to connect.  PAP, CHAP CHAT, etc.  pppconfig defaults are usually bang on.

Maybe look in your fedora configuration to see how it is configured (I do not know red hat - try /etc/ppp /etc/chatscripts /etc/peers /etc/network?)

Also, please show the output (for fun) of

sudo tail -f /var/log/messages

as you connect with sudo pon in another terminal.

---

### Post by jozmak on 2004-11-23
Success! 

This is what I think the problem was. When i run pppconfig the first time, i chose the option, dynamically retrieve IP addresses. From some reason ppp couldn't retrieve the correct numbers.  Then I rerun it, I chose static and entered the DNS numbers manually and the connection now works.  
But Wvdial still doesn't work and it displays exactly the same strange output I showed above. I think something still not quite right here.  The Network setting dialog doesn't work either. Only the pon command can connect to the internet.

Here is the pon log message, perhaps this may help identify some of the problems.

root@ubuntu:/home/mak # tail -f /var/log/messages
Nov 23 12:04:26 localhost chat[3843]: abort on (NO ANSWER)
Nov 23 12:04:26 localhost chat[3843]: abort on (DELAYED)
Nov 23 12:04:26 localhost chat[3843]: send (ATZ^M)
Nov 23 12:04:26 localhost chat[3843]: expect (OK)
Nov 23 12:04:26 localhost chat[3843]: ^M
Nov 23 12:04:26 localhost chat[3843]: OK
Nov 23 12:04:26 localhost chat[3843]:  -- got it
Nov 23 12:04:26 localhost chat[3843]: send (ATDT5144489294^M)
Nov 23 12:04:26 localhost chat[3843]: expect (CONNECT)
Nov 23 12:04:26 localhost chat[3843]: ^M
Nov 23 12:04:53 localhost chat[3843]: ATDT5144489294^M^M
Nov 23 12:04:53 localhost chat[3843]: CONNECT
Nov 23 12:04:53 localhost chat[3843]:  -- got it
Nov 23 12:04:53 localhost chat[3843]: send (\d)
Nov 23 12:04:54 localhost pppd[3841]: Serial connection established.
Nov 23 12:04:54 localhost pppd[3841]: Using interface ppp0
Nov 23 12:04:54 localhost pppd[3841]: Connect: ppp0 <--> /dev/ttyS0
Nov 23 12:04:56 localhost pppd[3841]: PAP authentication succeeded
Nov 23 12:04:56 localhost kernel: PPP BSD Compression module registered
Nov 23 12:04:56 localhost kernel: PPP Deflate Compression module registered
Nov 23 12:04:56 localhost pppd[3841]: local  IP address 66.201.246.63
Nov 23 12:04:56 localhost pppd[3841]: remote IP address 66.201.246.101
Nov 23 12:07:14 localhost pppd[3841]: IPCP terminated by peer
Nov 23 12:07:15 localhost pppd[3841]: LCP terminated by peer
Nov 23 12:07:15 localhost pppd[3841]: Hangup (SIGHUP)
Nov 23 12:07:15 localhost pppd[3841]: Modem hangup
Nov 23 12:07:15 localhost pppd[3841]: Connection terminated.
Nov 23 12:07:15 localhost pppd[3841]: Connect time 2.4 minutes.
Nov 23 12:07:15 localhost pppd[3841]: Sent 201 bytes, received 223 bytes.
Nov 23 12:07:15 localhost pppd[3841]: Exit.

jozmak

---

### Post by az on 2004-11-23
According to you isp's website and following the windows and mac setup directions, it uses dynamic ip addressing.  Hmmm.

Glad it works.  It's worth looking into.  Can you see how Fedora connects (assuming you still have it on your harddrive..) by doing the same thing (tail /var/log/messages -f) and looking at its /etc/ppp settings...



Thanks!

---

### Post by jozmak on 2004-11-24
Unfortunately, i was a bit too hasty and erased  Fedora  from my hard drive, so i cannot check its ppp configurations. 
But the wvdial output still puzzles me.

---

