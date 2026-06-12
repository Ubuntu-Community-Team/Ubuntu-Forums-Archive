---
title: "DSL speed"
date: 2009-06-24
forum: Hardware
---

### Post by dyess002 on 2009-06-24
( SOLVED ) OK here is the deal, I have DSL 512 KB down speed that I am paying for.
On a great day I can only get 52KB download speed.
I can go to a motel and get up to 300KB, I know my computer will handle at least 300KB so the problem has to be from the Router back to yhe Modem. Is there a way to find out what my download speed is from the router from the modem? the problem has to be there between the modem and the router. I am using a Linksys wgrg54 something like that.
I want the speed that I am paying for.

---

### Post by Herman on 2009-06-24
Plug your computer directly into the modem and see if that makes any difference?

---

### Post by lncoll on 2009-06-24
Seems there is no problem.
A 512 kbps. connection allows you to download at 50~55 kb/s.
The reason: 
Connection speeds are measured in kilo BITS per second and download speeds in kilo BYTES per second.
The difference 1 Byte = 8 Bits, also there is an overload trafic for protocols, headers, checksums etc. So a rule of the thumb is 10 bites per second of connection = 1 byte per second of download.

There are many speed testers in the net, I use to test in [http://www.speedtest.net](http://www.speedtest.net) , in this ones you can test your connection and download speed.

---

### Post by wojox on 2009-06-24
Can you connect via a wire and test speeds again? Assuming a wired test shows normal speeds you can blame the wireless connection. Can you test with another laptop? If it worked OK with another PC then it would be a problem with your new laptop.

Most wireless cards have a software option that will display quality of signal and stats on packets sent/received and errors.
check this display it might indicate a marginal signal and or interference causing poor through-put.

Wireless signals can be whacked by some wireless phones (2.4 Ghz band) and even your neighbors wireless base-station.
You could try to change the channel on the wireless transmitter. (it must be done from a wired connection to wireless router. You will need to logon to the router and supply the "admin" password.

the wireless router might also work better if it's not sitting on top of your desktop tower. Get it as far away from your other computers and TVs.

If none of these suggestions help - you have cause to call customer support.

---

### Post by dyess002 on 2009-07-11
[quote=lncoll;7507847]Seems there is no problem.
A 512 kbps. connection allows you to download at 50~55 kb/s.
The reason: 
Connection speeds are measured in kilo BITS per second and download speeds in kilo BYTES per second.
The difference 1 Byte = 8 Bits, also there is an overload trafic for protocols, headers, checksums etc. So a rule of the thumb is 10 bites per second of connection = 1 byte per second of download.


What is the connection the motel has that gives me 200KB and I have a uncle in Texas that has DSL and he is getting 200KB or better at his residence.  Could there be a setting to let you get more speed?

---

### Post by Herman on 2009-07-11
I'm no expert in networking or in telecommunications, so I hope you don't mind a human answer, or at least a human response here.

I was in our local small town electrical/electronics store quite a while back and I was just looking for a new router. They had one there for a reasonable price tag and it was a wireless modem router with ADSL2+ written on it as well. I didn't know what ADSL2+ was at the time, nor did I really understand a lot of the other stuff they had written on the plastic wrapped box containing the new electronic gadget. I only needed a router, but that was the only one in the store and the price was in the range I was prepared to pay so I though why not? 

Anyways, a few months down the track I got a phone call from my old ISP to ask if I want to sign up for a free six month trial of ADSL2 and if I like it, I can keep it and pay extra or go back to my old broadband speed and my bill won't be increased. So I agreed to try out ADSL2 for a while.

At first I didn't notice any great speed increase. I was still using my old ADSL modem that we were originally sold when we switched from dial-up to broadband. It doesn't have anything much written on it, I would need to google it up to find details about what speeds it is capable of.
One day I was in another room and I started up that new ADSL2+ wireless modem/router and it was then that I noticed the speed increase. I don't know why I hadn't thought of it earlier, other things on my mind I suppose, too many things to do. After that I began to enjoy the extra speed of ADSL2.

Another day I installed Ubuntu in a computer at a friend's house and it took hours and hours to get all the updates and install software. It's on my list to go and visit them again and try some experiments to find out why their internet is so slow. They have the same modem as my old one, but it shouldn't be that slow.
 I might try my ASUS Eeepc over at their place, it could be that their computer has an old slow ethernet card, or if it's the motherboard ethernet port, maybe they just have an old motherboard.

I have read that in some places in the world there is 'cable' internet, which I imagine is a lot faster than any kind of ADSL.

Anyhow, my point is, the internet speed we end up with is limited by whatever device is the slowest, whether that's our ISP's equipment or some piece of our own hardware.

... And then I suppose there's software - the ethernet driver, or how well Linux supports your ethernet card. Linux does an amazing job of supporting almost every ethernet card in the world, but there might be some that it's slow on or won't work maybe. I haven't found any, just using my imagination here.

Settings? Hmmm ... None that I know of.

---

### Post by Gemnoc on 2009-07-12
As lncoll said, all ISPs (internet service providers) measure speeds in megabits or kilobits. 52 kilo**bytes** per second is pretty normal for a 512 kilo**bit** per second connection.
[http://www.dslreports.com/faq/3758](http://www.dslreports.com/faq/3758)

Your 512Kbps connection is what is usually the lowest DSL speed offered. Your ISP may be offering a faster service at an extra cost. Your uncle or the motel may have a 3 or 5 megabits connection.

But keep in mind, with DSL there is a distance factor. The actual speed degrades with the distance from the telco office. Depending of the distance from your home to the telco office, high speed may not be available to your location. See link for some explanation:
[http://www.dslreports.com/faq/4676](http://www.dslreports.com/faq/4676)

My sister was paying for a 5Mbps connection, but she never got more than 1.5Mbps (I tested it many times over a period of months).

Regrettably, ISPs do not volunteer this information to potential customers... You will notice that they don't guarantee the speed. They always say: "up to <insert speed here>".

Your house phone wiring, especially if it's old, may also degrade the speed.

@ Herman

My ISP is also a cable company. My modem is plugged to the coaxial cable. The basic service is 600Kbps download and 128Kbps upload. Then the high speed service (the one I pay for) is 7.5Mbps download and 820Kbps upload. I get constant 900 kilobytes per second download speed, which is pretty sweet. Downloading the latest Ubuntu LiveCD takes me less than 15 minutes (not on the day of the release though ;) ). But my ISP offers even more speed: 10Mbps, 20, 30 and a whopping 50Mbps (but those last three are only available in limited areas for now).

The DSLReports site mentions 8Mbps as the maximum ADSL speed, but the local DSL provider here offers download speeds of up to 16Mbps, so I don't know what to think of that...

---

### Post by lncoll on 2009-07-12
As Gemnoc says:

> **Gemnoc said:**
> 
But keep in mind, with DSL there is a distance factor. The actual speed degrades with the distance from the telco office. Depending of the distance from your home to the telco office, high speed may not be available to your location. See link for some explanation:
[http://www.dslreports.com/faq/4676](http://www.dslreports.com/faq/4676)


The distance is the wire length from the modem in the telco central to your modem, also the wire age and quality affects, in the attached image you can see what to expect. (1 yard = 0.91 meters).

You can test the speed at home, at the motel and in your uncle home, with any of the speed testers in the net (use the same in any place).

If you speed is slower than expected:
[LIST=1]
[*]Check your home wires, must be dry and new, also the external connection box. Must be Telecom wires, not straight electricity wires. (the best is twisted pair).
[*]Claim for a new line to your telephone provider.
[/LIST]

If nothing of this solves the problem, and you are paying a faster connection as you get. Ask for a cheaper connection, you'll get the same speed for less.

---

### Post by Diamond.Dave on 2009-07-12
The other thing to consider (as alluded to before) is the connection to your street and/or house.  Some locations offer FTTP - Fiber to the Premeses - which will boost your speeds tremendously (but it's expensive).  Also, some service providers cheat and run copper to your house from tremendous distances without a relay/repeater, thus further degrading the signal.  If you are on wireless, then the distance from your WAP may also be degrading your service.

---

### Post by dyess002 on 2009-07-13
That is what I have been trying to say that there is something different with speeds and I believe it has something to do with what is putting out the speed, I know the router will send at least 54 mbs but I only get 50KB a sec so it has got to be a modem restriction.

---

### Post by lncoll on 2009-07-13
Ok, also there is another issue you must know:
There are two speeds to care. Internet speed (modem <-> internet) and local network speed (modem <-> PC).

May be you connect with your modem/router at 54 Mbps (WIFI connection) or 100 Mbps (ethernet wired connection). So if you have more than one PC at home, transfers between them can get 6 MB/s or 12 MB/s. But this is a local network transfer, internet is not involved.

Now if you transfer files from internet to your PC, two networks are involved, your local net and Internet. So the fastest speed you can get is the slowest of them.

Think you have two joined pipes a 4 inch one joined to a 1/8 inch one, the wide pipe is your local network, and the narrow is internet (the modem/router is the junction betweem pipes), so for internet connections does not care how wide is the pipe to your PC, the 1/8 pipe rules. ](*,)

---

### Post by benj1 on 2009-07-13
> **dyess002 said:**
> That is what I have been trying to say that there is something different with speeds and I believe it has something to do with what is putting out the speed, I know the router will send at least 54 mbs but I only get 50KB a sec so it has got to be a modem restriction.

what you need to keep in mind is that the network is only as good as its weakest link, in telecoms thats copper wires, and the so called final mile. 
yes everything in your house (modem,router,pc) could handle multiple 10's of megabytes of data, but if it doesn't receive that it won't be able to make use it. 
on the other end the fibre optic backbone can probably deal with GBs of data / sec, the problem is, is that it is expensive to install in up to every bodies house, so copper is used, which unfortunately isn't very good for carrying digital signals, due to degradation etc, that is why you don't get the speed advertised. although it is theoretically possible if you live right next to a telephone exchange (which is why they can advertise the higher speeds).

---

### Post by PatrickVogeli on 2009-07-13
Yeah of course you have a modem restriction. You are paying 512 kbps, and you are getting 512 kbps. Where's the problem? The speed is being limited by your ISP, but you can't do anything about that. Not even getting a new modem router will solve that, since the limit isn't in modem, but in the company's server of whatever. Have I said solve? Sorry, there's nothing to solve. You simply can't bypass that limit. Solution? Paying and upgrading to a faster service, like 1Mbps, 2, 3 or even 10Mbps or 20Mbps.

For getting speeds in the order of 200Kb/s you would need a 1600 kbps line. Probably they have a 2 Mbps line.

Another thing to consider is wifi 54 Mbps or ethernet's 100 Mbps or 1000 Mbps. Those speeds are between the router and some computer, nothing to do with the line speed at all.

---

### Post by PatrickVogeli on 2009-07-13
Oh, btw, you're getting acceptable speeds: with a 512kbps line, the maximum theoretical speed would be 64 kB/s, and you are getting 52, which is quite good.

---

### Post by dyess002 on 2009-07-13
> **Gemnoc said:**
> As lncoll said, all ISPs (internet service providers) measure speeds in megabits or kilobits. 52 kilo**bytes** per second is pretty normal for a 512 kilo**bit** per second connection.
[http://www.dslreports.com/faq/3758](http://www.dslreports.com/faq/3758)

Your 512Kbps connection is what is usually the lowest DSL speed offered. Your ISP may be offering a faster service at an extra cost. Your uncle or the motel may have a 3 or 5 megabits connection.

But keep in mind, with DSL there is a distance factor. The actual speed degrades with the distance from the telco office. Depending of the distance from your home to the telco office, high speed may not be available to your location. See link for some explanation:
[http://www.dslreports.com/faq/4676](http://www.dslreports.com/faq/4676)

My sister was paying for a 5Mbps connection, but she never got more than 1.5Mbps (I tested it many times over a period of months).

Regrettably, ISPs do not volunteer this information to potential customers... You will notice that they don't guarantee the speed. They always say: "up to <insert speed here>".

Your house phone wiring, especially if it's old, may also degrade the speed.

@ Herman

My ISP is also a cable company. My modem is plugged to the coaxial cable. The basic service is 600Kbps download and 128Kbps upload. Then the high speed service (the one I pay for) is 7.5Mbps download and 820Kbps upload. I get constant 900 kilobytes per second download speed, which is pretty sweet. Downloading the latest Ubuntu LiveCD takes me less than 15 minutes (not on the day of the release though ;) ). But my ISP offers even more speed: 10Mbps, 20, 30 and a whopping 50Mbps (but those last three are only available in limited areas for now).

The DSLReports site mentions 8Mbps as the maximum ADSL speed, but the local DSL provider here offers download speeds of up to 16Mbps, so I don't know what to think of that...





Thanks Gemnoc for the explanation, Is there a device that can measure speed from the box into the modem and from the modem to the router?
So I can find where I am loosing speed or if I am at all.

---

