---
title: "What ISP can I use with Ubuntu?"
date: 2008-08-07
forum: General Help
---

### Post by lyndsey80 on 2008-08-07
I had Three mobile but that didn't work with Ubuntu then I was going to get Virgin broadband but they only accept customers with Windows and that seems the same with most ISP - what one can I actually use?

---

### Post by Krupski on 2008-08-07
> **lyndsey80 said:**
> I had Three mobile but that didn't work with Ubuntu then I was going to get Virgin broadband but they only accept customers with Windows and that seems the same with most ISP - what one can I actually use?

That really makes no sense to me. If you get cable based broadband Internet, the ISP provides you with a cable modem. The cable modem usually has a USB port on it and a standard RJ-45 network connector.

You should not need any software from the ISP... just plug your PC into the cable modem and use DHCP to get your IP address and DNS servers.

Some ISP's want to install their software on your computer so that your traffic goes through THEIR proxy server. You don't need that.

If you want to go wireless, just use a standard wireless router and again just plug it into the cable modem.

There is no reason that any ISP should require you to use a particular OS. The Internet is just a stream of data... who cares WHERE it goes to? Bits be bits.

-- Roger

---

### Post by chalewa on 2008-08-07
> **Krupski said:**
> That really makes no sense to me. If you get cable based broadband Internet, the ISP provides you with a cable modem. The cable modem usually has a USB port on it and a standard RJ-45 network connector.

You should not need any software from the ISP... just plug your PC into the cable modem and use DHCP to get your IP address and DNS servers.

Some ISP's want to install their software on your computer so that your traffic goes through THEIR proxy server. You don't need that.

If you want to go wireless, just use a standard wireless router and again just plug it into the cable modem.

There is no reason that any ISP should require you to use a particular OS. The Internet is just a stream of data... who cares WHERE it goes to? Bits be bits.

-- Roger



While all of this is true, a lot of ISP's require that you have a windows box to 'install' the modem on to make sure that they can get an IP address, and to be sure that the line actually works. 

Essentially a lot of ISPs don't want to teach their techs how to type ifconfig into a terminal box. 

That being said, go with what ever ISP you like, and maybe try to have a windows box lying around just so that the tech can ensure the connection is working

---

### Post by Krupski on 2008-08-07
> **chalewa said:**
> While all of this is true, a lot of ISP's require that you have a windows box to 'install' the modem on to make sure that they can get an IP address, and to be sure that the line actually works. 

Essentially a lot of ISPs don't want to teach their techs how to type ifconfig into a terminal box. 

That being said, go with what ever ISP you like, and maybe try to have a windows box lying around just so that the tech can ensure the connection is working

Agreed... but the ISP can check on their end if the cable modem is up, what the signal levels are, whether it got assigned an IP address, etc...

There should really be no need to actually hook a computer to the modem to see if it's working.

And, as you said, simply using 'ifconfig' or 'ping anyone.com' will tell you right away if it's working.

I would think that cable companies would have a little "box" that is battery powered, has a simple LCD screen and an RJ-45 port. They plug it into the modem, the box runs a small canned set of tests and says "Good" or "Fail" on the LCD.

Heck... I could build something like that with a 68HC11 microcontroller board and a few days of programming!

---

### Post by chalewa on 2008-08-07
Again, I agree with all of this, but the problem is that there is just not enough demand for ISP companies to go through all of this. 

There are only a few people out there, relative to mac and windows users, who use linux, so it just doesn't make sense for ISPs to 'support' these additional OS. 

I think that another major issue is that by doing it the way they do now, they prevent a lot of people from calling in to them saying 'your tech just left, but i can't get on the internet blah blah blah'

---

### Post by ChumleyEX on 2008-08-07
So borrow someones laptop on the day they come out to install. /done

---

### Post by y@w on 2008-08-07
The ISP that I'm on just had me make sure the router had an IP and could connect out. When asked about my operating system I said "uh, all of them.." :)

---

### Post by hyper_ch on 2008-08-07
run a windows in a vm if they insist on you having windows.

---

### Post by alphane on 2008-08-07
I'm a UK customer with Virgin Media Cable Broadband.

They supply you with a cable modem, which I have hooked into a wireless modem, and so on from there.

It will be a similar scenario with all other UK based providers, cable based or not, was previously with ADSL provider Pipex, still using Ubuntu.

They will only provide tech-support for windows based systems, and if they offer any free software, like anti-viruses etc, then they will also obviously be for windows based systems.

Hope this helps.

---

### Post by Stunts on 2008-08-07
You guys are giving a nice set of hints, but honestly I think the OP was talking about Mobile Internet.
In this case you will usually need very specific software to handle the USB or XpressCard that they provide.
There are ways to make them work under linux. I had a link for the TMN provider here in Portugal (it's in Portuguese, but I can provide it anyway if you still want it).
It can be tricky and involves a lot of terminal typing to get to work the first time and then some scripting to automate, and you will likely need software that is not on the repros for mode switching, but in theory you should be able to connect *ANY* of those things using linux...

---

### Post by Trollslayer on 2008-08-08
Ubuntu + Virgin here, you don't need to install anything on the PC to use it.
Set the network connection to DHCP and plug into the ethernet port on the cable modem.

---

### Post by y@w on 2008-08-08
From my experience most of the wimax providers all just give you a wireless bridge that you plugin via ethernet so you shouldn't need drivers to go that route.

---

### Post by dje on 2008-08-08
tiscali + ubuntu here. although if you use their router i think it needs an initial setup with windows but i just used my existing netgear

dje

---

### Post by Mgiacchetti on 2008-08-08
comcast came out and "installed" a cable modem on my ubuntu box without having to use windows, just opened firefox and went to google to make sure i was online.

---

### Post by Sycron on 2008-08-08
Some ISP-s assign IP by verifing your MAC address , so you may 'hack' your own MAC address with **macchanger**.
```
$sudo apt-get install macchanger
```

---

### Post by eentonig on 2008-08-08
Are we (the OP) talking about a home based internet solution? Or is it a UMTS/GPRS alike solution for use while on the road?

---

