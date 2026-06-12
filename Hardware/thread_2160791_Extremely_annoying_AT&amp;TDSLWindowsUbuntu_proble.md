---
title: "Extremely annoying AT&amp;T/DSL/Windows/Ubuntu problem"
date: 2013-07-08
forum: Hardware
---

### Post by Buntu Bunny on 2013-07-08
ISP - AT&T
ethernet connection
modem - Westell 6100
dual boot with Windows 7

This has been going on for the past 5 days. At least once per day, my DSL goes out. The first two times, I booted into Windows, called AT&T support, went through the automated directions and had to reinstall the modem. (I've learned not to call AT&T support in Ubuntu or Xubuntu, because they don't "support" Linux). 

It's continued to go out at least once a day, since. The difference is that now, I simply have to call AT&T (with my computer in Windows), and the DSL will wake up within seconds of the call connecting. After that I can reboot into Xubuntu and go about my internet business until the modem's DSL light starts flashing red again. 

If I try this from my Xfce desktop, it wants me to reinstall the modem except that it never completes the steps; the browser screen hangs up at the first step indefinitely. 

Is this a firmware / driver problem? I'm not sure where to turn except here. AT&T won't help unless I'm willing to pay something like $200 for specialized support for my OS.

---

### Post by dino99 on 2013-07-08
**** Verizon DSL does not like the DHCPDISCOVER request.  *****  
not a recent post, but ... [http://www.dslreports.com/forum/r20741331-Linux-Ubuntu-Westell-6100-Verizon-DSL](http://www.dslreports.com/forum/r20741331-Linux-Ubuntu-Westell-6100-Verizon-DSL)

[https://www.google.fr/#q=ubuntu+westell+6100&source=lnt&tbs=qdr:y&sa=X&ei=FMraUdrTDoW2hQeS_4DoCA&ved=0CBkQpwUoBQ&bav=on.2,or.r_qf.&bvm=bv.48705608,d.d2k&fp=2049875acbfb0313&biw=1674&bih=925](https://www.google.fr/#q=ubuntu+westell+6100&source=lnt&tbs=qdr:y&sa=X&ei=FMraUdrTDoW2hQeS_4DoCA&ved=0CBkQpwUoBQ&bav=on.2,or.r_qf.&bvm=bv.48705608,d.d2k&fp=2049875acbfb0313&biw=1674&bih=925)

---

### Post by Buntu Bunny on 2013-07-08
> **dino99 said:**
> **** Verizon DSL does not like the DHCPDISCOVER request.  *****  
not a recent post, but ... [http://www.dslreports.com/forum/r20741331-Linux-Ubuntu-Westell-6100-Verizon-DSL](http://www.dslreports.com/forum/r20741331-Linux-Ubuntu-Westell-6100-Verizon-DSL)

[https://www.google.fr/#q=ubuntu+westell+6100&source=lnt&tbs=qdr:y&sa=X&ei=FMraUdrTDoW2hQeS_4DoCA&ved=0CBkQpwUoBQ&bav=on.2,or.r_qf.&bvm=bv.48705608,d.d2k&fp=2049875acbfb0313&biw=1674&bih=925](https://www.google.fr/#q=ubuntu+westell+6100&source=lnt&tbs=qdr:y&sa=X&ei=FMraUdrTDoW2hQeS_4DoCA&ved=0CBkQpwUoBQ&bav=on.2,or.r_qf.&bvm=bv.48705608,d.d2k&fp=2049875acbfb0313&biw=1674&bih=925)

Dino99, thank you for replying. I've looked at your links and admit they are over my head, so it will take me awhile to read through and decipher. At least it's a start.

I know that on the AT&T firmware page, it warns that AT&T firmware is not the same as Verizon and cannot be interchanged. Of course, I'm not certain this is a firmware problem, but I think I'd better take advice for Verison DSL with a grain of salt.

---

### Post by Buntu Bunny on 2013-07-08
It turns out that the first link was addressing a problem different than mine.

The second link uncovered nothing new in terms of my previous searches. The problem persists, so I am still in search of an answer.

---

### Post by TransitMan on 2013-07-09
Are you connecting directly to the modem from the computer, or via a router?

From your description, it sounds like your losing sync at the DSLAM. Instead of calling AT&T support, or rebooting into Windows when this happens, how about just unplugging the modem and then plugging it back in.

---

### Post by Buntu Bunny on 2013-07-09
> **TransitMan said:**
> Are you connecting directly to the modem from the computer, or via a router?

From your description, it sounds like your losing sync at the DSLAM. Instead of calling AT&T support, or rebooting into Windows when this happens, how about just unplugging the modem and then plugging it back in.

TransitMan, thank you for your response. The modem is plugged into the computer. I've had this arrangement for years and have made no alterations, so this twice a day situation is tiresome. I've gone through all the steps, including unplugging and/or restarting the modem and rebooting my PC. I've gone though the AT&T web diagnostics page and its tests tell me that the ADSL sync test fails during these times. The only solution so far is to call AT&T support. Within seconds of connecting, the modem is back online. I don't have to actually do anything or talk to anyone, just call while booted into Windows. Puzzling, eh?

---

### Post by Bashing-om on 2013-07-09
Buntu Bunny; Hi !

Here's a thought.
A particular MAC is tied to the ISP's account. I found this out when trying to bring up another computer on Suddenlink's Arris modem .. found I had to use a router, cloned mac address as that original machine.
Is it possible that the MAC changes when switching OS's ?
That said what results if you get a new lease on the IP , when you experience the problem?
```
dhclient
```

Makes one wonder what has changed at the ISP point of presence in that the situation has only recently developed.

[INDENT][INDENT]gotta be a cause[/INDENT][/INDENT]

---

### Post by Buntu Bunny on 2013-07-09
Bashing-on, hi(!) and thank you!

Here's what I get 

```

leigh@leigh-CM1740:~$ sudo dhclient
[sudo] password for leigh: 
RTNETLINK answers: File exists
```

I did check the MAC address in both Linux and Windows and they are the same.

AT&T is in the process of upgrading their net webmail, if that makes a difference.

---

### Post by Bashing-om on 2013-07-09
Buntu Bunny;

Wow !... never seen that result from "dhclient" ... be more than a bit before I am willing to test on my system ( wife is beside me on her box, do not wish to cause an interruption to her links)..
I will respond as soon as possible.

[INDENT][INDENT]we be look'n
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-07-09
Buntu Bunny; Hey;

Uncle Google says:
1. Config files;
a) /etc/resolve.conf
b) /etc/network/interfaces

(I am aware that there are changes in the method network manager is integrated and others, I have done some searching looking for those docs, not found them again to this time.)

2. Lots of comments that one can not have 2 instances of an interface accessing the gateway.
for instance; see:
[thread]1981219[/thread]

else to consider :
All I can think of presently is for some reason the interface is not being relinquished from either operating system when the session is terminated ?? 

[INDENT][INDENT]dont know but would like too[/INDENT][/INDENT]

---

### Post by Buntu Bunny on 2013-07-09
Bashing-om, thank you so much for your help. 

I'll start with your list for my research. These are some things I'm going to have to study up on as it's new territory for me. 

> **Bashing-om said:**
> else to consider :
All I can think of presently is for some reason the interface is not being relinquished from either operating system when the session is terminated ?? 

I've had it happen in Ubuntu, also when the computer is turned off, as in when I go to boot up in the morning the DSL is out. Initially I assumed the problem was related to the weather. Bad weather frequently knocks out my internet, but there have never been residual problems, except this time it's been raining all week.

---

### Post by Bashing-om on 2013-07-09
Buntu Bunny; Well ....

Let me tell you .. wiring problems is a definite possibility for an intermittent situation...years back had that type of problem ... and finally found it .......
ants in the connection box at the gangwire on the highway ! For real ants !

But still need to clear an inhouse config situation .. something may have changed the config files... used to be that Network manager wrote to /etc/NetworkManager/NetworkManager.conf ... but that file has been depreciated .. and have not found again what took it's place.

We need to be in the position that we can prove to AT&T that the problem is not "inhouse".

[INDENT][INDENT]we can whoop this[/INDENT][/INDENT]

---

### Post by steeldriver on 2013-07-09
I fought with DSL issues for a LOOONG time before finally switching to a cable based internet service - same as you I had weather dependence (turned out to be old cotton-insulated wires)

I agree wih TransitMan, it sounds a lot like a DSL sync / noise margin issue - my best advice is to bug your ISP (you MUST get past the 'tier 1' "have you made sure it's plugged in" folks) until they agree to to do a noise margin test on your line, and if necessary adjust the target sync rate at the DSLAM - you will need to sacrifice a little bit of potential connection bandwidth in order to get a stable connection

[There are *some* DSL modems that can be configured from the customer side to do that e.g. the Thomson Speedtouch modems via DMT --> [http://kitz.co.uk/routers/DMTv7.htm](http://kitz.co.uk/routers/DMTv7.htm) but otherwise it has to be done by the ISP]

---

### Post by VMC on 2013-07-09
I have the exact same setup, only my isp is Verizon. I had issues a while back and it was the modem. I've replaced two alread and have new ones on hand. No problems in a couple of years.

Your "ifconfig" will reveal your isp address "inet address. If you take that address and use it as a URL link it may reveal you Westell modem options. 
**For example**   --> 192.164.1.48  What ever your is try replacing the last digit with a one. 192.164.1.1

I had problems with PPoE, which is East Coast, vs BRIDGED which is West Coast. If Westell 6100 ask for a password, the default is :  *Login: admin, Password: admin*

---

### Post by Buntu Bunny on 2013-07-09
> **Bashing-om said:**
> Let me tell you .. wiring problems is a definite possibility for an intermittent situation...years back had that type of problem ... and finally found it .......ants in the connection box at the gangwire on the highway ! For real ants !

Bashing-om, that is too funny. I reckon it could have been worse!

> **Bashing-om said:**
> But still need to clear an inhouse config situation .. something may have changed the config files... used to be that Network manager wrote to /etc/NetworkManager/NetworkManager.conf ... but that file has been depreciated .. and have not found again what took it's place.

Yes, I found that file to be empty as well.

> **steeldriver said:**
> I fought with DSL issues for a LOOONG time before finally switching to a cable based internet service - same as you I had weather dependence (turned out to be old cotton-insulated wires)

I agree with TransitMan, it sounds a lot like a DSL sync / noise margin issue - my best advice is to bug your ISP (you MUST get past the 'tier 1' "have you made sure it's plugged in" folks) until they agree to to do a noise margin test on your line, and if necessary adjust the target sync rate at the DSLAM - you will need to sacrifice a little bit of potential connection bandwidth in order to get a stable connection

What I did for now, was to check the connection online at the AT&T website. Everything passed except the ATM signal test.

```
Check ATM cell-delineation 	Pass
Check ATM signal 	Fail
Perform ATM OAM segment ping 	Pass
Perform ATM OAM end to end ping 	Pass 
```

At this point, I'm not sure if that's relevant, however. 

> **VMC said:**
> Your "ifconfig" will reveal your isp address "inet address. If you take that address and use it as a URL link it may reveal you Westell modem options. **For example**   --> 192.164.1.48  What ever your is try replacing the last digit with a one. 192.164.1.1

Thanks VMC, I tried that but it gave me a no such address response. This is the second modem I've had. I replaced the first one when I had other connection issues.

---

### Post by VMC on 2013-07-10
Try "192.168.1.1"

Copy & paste into you browser URL. Nothing else but what's between the quotes. See if you can access the Westell modem.

Edit: AT&T may have another access point if the above address doesn't work. I'm surprise AT&T didn't have you access the modem from the start of your problem. That usually determines the point of trouble - in or out.

---

### Post by Buntu Bunny on 2013-07-10
> **VMC said:**
> Try "192.168.1.1"

Copy & paste into you browser URL. Nothing else but what's between the quotes. See if you can access the Westell modem.

Yes, I tried that one too, as you suggested. Firefox gave me an "unable to connect" for that as well.

> **VMC said:**
> Edit: AT&T may have another access point if the above address doesn't work. I'm surprise AT&T didn't have you access the modem from the start of your problem. That usually determines the point of trouble - in or out.

I believe you're correct about that. The address on the bottom of the modem is 192.168.1.254. I get the connection info and the ability to check my connection for Ethernet, ADSL, ATM, PPPoE. Authentication, IP, and DNS. The only fail is the ATM signal test. There is also a page for advanced configuration.

*I ought to add that since our weather cleared up, my modem has behaved nicely and the DSL stays online,

---

### Post by VMC on 2013-07-10
> **Buntu Bunny said:**
> ...
*I ought to add that since our weather cleared up, my modem has behaved nicely and the DSL stays online,

A telltale sign! It appears to be AT&T problem. Did you ask them to test the line strength? Its a simple automatic test anyone at the command center can perform.
That was another issue that I had, and the tech said they detected static on the line. The next day, they replaced the drop line and all was good after that.

---

### Post by Buntu Bunny on 2013-07-10
> **VMC said:**
> A telltale sign! It appears to be AT&T problem. Did you ask them to test the line strength? Its a simple automatic test anyone at the command center can perform.
That was another issue that I had, and the tech said they detected static on the line. The next day, they replaced the drop line and all was good after that.

Thank you VMC. I have not asked about that yet but will look into it!

---

### Post by Buntu Bunny on 2013-09-25
I'm finally going to mark this problem as solved. Thanks to everyone who responded in this thread, I was at least able to figure out that the problem wasn't with me and my set up. The problem was with my service provider. Even though I had them run the tests suggested in this thread, they still claimed the problem was at my end and wanted me to pay for a technician to come out and fix it. Last week we changed our ISP and, can you imagine this, the problem was solved! Plus, for the same monthly price we have amazingly faster internet and crystal clear telephone. Good-bye AT&T and hello world!

---

