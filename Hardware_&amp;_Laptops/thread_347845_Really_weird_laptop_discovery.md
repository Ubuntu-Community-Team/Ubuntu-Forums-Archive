---
title: "Really weird laptop discovery"
date: 2007-01-27
forum: Hardware &amp; Laptops
---

### Post by Henry Rayker on 2007-01-27
Well, this is my first notebook computer ever, so a lot of the way it's put together is weird to me...but this tops everything.

When I did a lsusb, I always saw 4 USB lines, but I only have 3 ports on the side of my computer. I thought that was strange, but ignored it...today, though, I was poking around (cleaning dust out of the fan etc) and I realized there was a really small panel I had never noticed before...it's held on with one screw and butts up right next to the harddrive.

I took the panel off, not sure what to expect...it's a usb port, mounted parallel with the bottom of the computer...I hooked up a USB extension cord to it and plugged my wireless usb dongle into it and booted up...it works!

My question though is: is this common? What in the world is it doing there? Honestly, if I took the dongle apart, I could probably JUST BARELY fit the dongle in this little compartment with a little work. Anyone have any idea what use this could possibly serve?

A small side question: I noticed I have a minipci slot with an antenna routed incredibly close to it. Do any of you have any experience with installing internal wireless adapters? Any tips/suggestions for one that works well? All of my wireless experience is with Ralink driver sets and I can't get them to work with the Network-Manager...

---

### Post by ianthepetrock on 2007-01-27
Could it be for a docking station?

---

### Post by Henry Rayker on 2007-01-27
You know, I thought that it's possibly for a docking station...but to use it, you'd have to remove the panel, put the laptop down onto the station and then slide it to the left to plug the USB in. As I said, I'm very new to laptops, so I'm not sure how these stations tend to work.

---

### Post by RandomJoe on 2007-01-27
I have read a couple of places recently that some manufacturers are doing this just for something like you mention - provide an "internal" device that is really just a USB device, perhaps without a protective case to fit it inside.  Kind of like a miniPCI slot.

---

### Post by sloggerkhan on 2007-01-27
On my system I have no such access panel, but many things, such as bluetooth, thought internal, show up as being on the USB bus.

---

### Post by FreakTech on 2007-01-28
What kind of laptop is it?  Most laptops put the internal wireless card in the same compartment as the extra memory socket.  As far as the USB port I have no idea.  I work on all types of laptops on a daily basis and haven't ever seen that.

---

### Post by Henry Rayker on 2007-01-28
I don't remember who made this laptop. I bought it because I was stuck on campus a lot with a bunch of programming assignments to take care of...The spot where the USB plug is is literally JUST BARELY long enough that you can get a plug in there. I have a second RAM slot as well as a miniPCI slot. The lsusb output lists 3 Buses, 2 have only one Device, the other has 2 (one of which is that internal one).

I'll take a pic of the spot if I get a chance.

---

### Post by FreakTech on 2007-01-28
Yeah that would be the slot for the internal card.  Pretty simple to install.

---

### Post by Henry Rayker on 2007-01-28
> **FreakTech said:**
> Yeah that would be the slot for the internal card.  Pretty simple to install.

I assume you mean the miniPCI is the slot for the internal card. Do you have a suggestion on which card I should go with?

---

### Post by FreakTech on 2007-01-28
I am currently running an intel PRO/Wireless ABG 3945.  Works great and is functional right out of the box with ubuntu.  I haven't tried any other ones with ubuntu, but broadcom makes some good ones too.

---

### Post by maniacmusician on 2007-01-28
> **FreakTech said:**
> I am currently running an intel PRO/Wireless ABG 3945.  Works great and is functional right out of the box with ubuntu.  I haven't tried any other ones with ubuntu, but broadcom makes some good ones too.
I've heard that broadcoms require ndiswrapper for them to get any functionality, and it's usually not complete functionality.

That holds true for my broadcom (Belkin) card. Doesnt work without ndiswrapper.

edit: I have 2 broadcom cards, one for my desktop and once pcmcia card for my older laptop. Both require ndiswrapper

---

### Post by GameManK on 2007-01-28
I haven't seen anything like that on a laptop (I mostly work with Dells) but I've seen an HP desktop where it had a backplate that covered up one of the USB ports making it seem like there was only one when there were two.

---

### Post by atihimself on 2007-01-28
maybe its for small flash memory, you can use it as adittional ram i think, but i'm not shure

---

### Post by mips on 2007-01-28
> **Henry Rayker said:**
> 
A small side question: I noticed I have a minipci slot with an antenna routed incredibly close to it. Do any of you have any experience with installing internal wireless adapters? Any tips/suggestions for one that works well? All of my wireless experience is with Ralink driver sets and I can't get them to work with the Network-Manager...

Installing mPCI adater is a simple 1 minute job.

See the picture in this post  [http://ubuntuforums.org/showpost.php?p=1780471&postcount=17](http://ubuntuforums.org/showpost.php?p=1780471&postcount=17)
[COLOR=Red][B]
Warning: [/B][/COLOR]What laptop brand/model do you have ?
Some brands implement BIOS white lists that prevent you from installing just any card. They force you install their branded cards only.

---

### Post by RandomJoe on 2007-01-28
> **Henry Rayker said:**
> A small side question: I noticed I have a minipci slot with an antenna routed incredibly close to it. Do any of you have any experience with installing internal wireless adapters? Any tips/suggestions for one that works well? All of my wireless experience is with Ralink driver sets and I can't get them to work with the Network-Manager...
Hm, I missed the side note last time I read this!  I have used a couple of miniPCI cards in my Dell laptops, but they were both Dell cards so worked.  Mips' comment would be a good one to note!

The B/G card I have is a Broadcom (lspci says BCM4306, think Dell calls it a TrueMobile 1350), but I've never had any issues with it - used ndiswrapper to run it with the Windows drivers suggested on the ndiswrapper site (they changed on me once, drove me crazy trying to get it to work on a new install until I revisited the site and got the new suggested drivers).  The card has been nicely dependable, although the signal is weak due to the lousy antenna location in the computer.

I also have a B card (TrueMobile 1130 IIRC) that uses some open drivers (been too long, don't remember which ones) but it was flakier - would only associate once, after which you had to unload/reload the modules, so using it anywhere but someplace I had already created a wireless profile for was a right PITA.

I far prefer internal cards - nothing hanging off the side of the machine, and it is always ready to go.  One argument against is that if you don't need wireless, being able to completely remove the card means NO power is wasted on an unused device.

---

### Post by mips on 2007-01-28
> **RandomJoe said:**
> Hm, I missed the side note last time I read this!  I have used a couple of miniPCI cards in my Dell laptops, but they were both Dell cards so worked.  Mips' comment would be a good one to note!


If you own a Dell you are safe as they have not gone down this idiotic route yet. HP & IBM however are the culprits and I do not know who else. Sometimes there are workarounds like a laptop bios hack or hacking the wireless cards firmware as it was in my case.

---

### Post by Henry Rayker on 2007-01-28
I bought the laptop from [here]("http://unitedmicro.com/cgi-bin/nt_m.cgi?AMD") The model I got is very close to, if not exactly, a N259KI. I don't think they'd have a BIOS whitelist but, if they do, I could always go with the Intel® PRO/Wireless 2200BG that they would have installed had I purchased it at the time.

Does anyone have any experience wiith the Intel PRO/Wireless 2200BG? Ideally, I'd like it to be able to roam networks...or at very least, allow me to configure it for multiple networks and, it would automatically connect if one of those is available.

---

### Post by rado_london on 2007-01-28
I only have 4 USB ports and this is the output of lsusb: 
```
rado@linux-laptop:~$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 005: ID 049f:000e Compaq Computer Corp. Internet Keyboard
Bus 001 Device 004: ID 046d:c518 Logitech, Inc.
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

```

Does it mean that I have 7 USB ports?

---

### Post by mips on 2007-01-28
> **Henry Rayker said:**
> I bought the laptop from [here]("http://unitedmicro.com/cgi-bin/nt_m.cgi?AMD") The model I got is very close to, if not exactly, a N259KI. I don't think they'd have a BIOS whitelist but, if they do, I could always go with the Intel® PRO/Wireless 2200BG that they would have installed had I purchased it at the time.

Does anyone have any experience wiith the Intel PRO/Wireless 2200BG? Ideally, I'd like it to be able to roam networks...or at very least, allow me to configure it for multiple networks and, it would automatically connect if one of those is available.


You should be fine, it's usually only the big brand vendors that do this stupid white listing crap.

Just for the record, even though you buy a genuine Intel card it will not work in a HP. You must buy the HP Intel one in order for it to work. They change a few bytes in the card firmware to give it a HP specific ID.

The Intels are generally a safe bet but i don't have any experience as i have not used mine though. There are newer version than the 2200 available.

---

### Post by bonzodog on 2007-01-28
> **rado_london said:**
> I only have 4 USB ports and this is the output of lsusb: 
```
rado@linux-laptop:~$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 005: ID 049f:000e Compaq Computer Corp. Internet Keyboard
Bus 001 Device 004: ID 046d:c518 Logitech, Inc.
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

```

Does it mean that I have 7 USB ports?

No, you have 5. look at the BUS numbers. there are three lines for bus 1, which has a device or two attached to it.

---

### Post by K.Mandla on 2007-01-28
I'm just going to shift this to Hardware and Laptops. ;)

---

### Post by Henry Rayker on 2007-01-28
> **bonzodog said:**
> No, you have 5. look at the BUS numbers. there are three lines for bus 1, which has a device or two attached to it.

I actually have 3 Buses, but 4 physical ports...the "mystery port" I have on the back is tied to bus 2.

If rado_london's output is from a PC, there are probably some internal pinouts (on the mobo for front panel, on some sound cards, some other cards as well) which are showing up.

---

### Post by Henry Rayker on 2007-01-28
hrrmmmm...editing my post posted a second time =\

---

### Post by rado_london on 2007-01-28
> **Henry Rayker said:**
> I actually have 3 Buses, but 4 physical ports...the "mystery port" I have on the back is tied to bus 2.

If rado_london's output is from a PC, there are probably some internal pinouts (on the mobo for front panel, on some sound cards, some other cards as well) which are showing up.

Its HP Pavilion dv4000 laptop.

---

### Post by Henry Rayker on 2007-01-28
> **rado_london said:**
> Its HP Pavilion dv4000 laptop.

That's odd, because you have 5 buses which lends me to believe that you have, at least, 5 ports

---

### Post by mips on 2007-01-28
> **Henry Rayker said:**
> That's odd, because you have 5 buses which lends me to believe that you have, at least, 5 ports

5 buses don't always translate to 5 physical external ports.

---

### Post by xmastree on 2007-01-28
This has me thinking. Whenever I do lsusb, I always see an 'empty' slot...
My laptop is a Toshiba Satellite Pro 3400 (quite old, Celeron 600) which has one USB port at the back.

lsusb with nothing in there gives:

**Bus 001 Device 001: ID 0000:0000**


Plug in my card reader (no card in it)

[B]Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. 
Bus 001 Device 001: ID 0000:0000 [/B]

Does this mean I may have a second one buried somewhere, like the OP?

---

