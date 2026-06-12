---
title: "I'm building a home server and I need advice"
date: 2013-01-04
forum: Hardware
---

### Post by ivotkl on 2013-01-04
Hello, I'm planning to buy a new box mainly to use with Ubuntu for media center and server/remote access.

I might be using it in a bigger project later on ("playing" with different type of servers. I would also need advice about that but this would be the wrong forum. Will post a thread on correct one once I buy the components), so I'm thinking to make a good inversion that could last on the long run. I checked on MSI's website and everything chosen seems to be compatible. I just wanted to know what do you think about it.

HW chosen is:

HBP900SM	PSU 900W 24P SATA SENTEY
A55M-P35	MOT MSI FM1 A55M-P35
A63670	CPU AMD APU A6-3670 2.7GHZ 4MB FM1
KHX1600C9D3B1/4G	MEM DDR3 4GB 1600MHZ KINGSTON
KHX1600C9D3B1/4G	MEM DDR3 4GB 1600MHZ KINGSTON
AGT3-60G	HD SSD 60GB OCZ SATA3 2.5
WD5000AAKX	HD 500GB W.DIGITAL 7200 SATA3 16MB
R5450MD1GD3H/LP	VGA PCI-E 1GB R5450 MSI DDR3

I already have a low cost case to put everything in and I can buy an extra cooler to prevent overheating. I have one installed already, any advice on brands of second one? Again, I'm trying to make it as low as I can for the time being but with good quality components.
So, I don't want to spend 1 USD for something that won't last (just saying).

Is PSU too much? If so I can ask retailer guy if he can get a lower one to save some money. I'm also planning to cut some bucks on final price and use just the 500 GB HDD and only one Memory module (I can always buy more modules and HDDs when I can, right? =P)

Also, if my server knowledge in the future is good enough, I might contact some geeky friends and make something bigger. Maybe found a company or something. So, this computer in the end might be on 24/7. Any advice on low power consumption components? As it would work as a headless server, I'll just go ahead and remove dedicated GPU to start with power saving. I know there are some "green" HDDs. Would performance be highly affected? (I'm assuming this based on the fact that it might be a 24/7 server).

Any help would be highly appreciated.

---

### Post by 2F4U on 2013-01-05
I would think that the PSU is to big and 400 - 500 W would be sufficient. Since the AMD APU has an ATI graphics card incorporated, you could think about whether you need the dedicated graphics card (R5450).
I don't know your case, but considering air flow you might think about installing additional case fans. But thats something that can be done once the base system is ready.

---

### Post by ivotkl on 2013-01-07
2F4U, Thank you for the reply.

Sure, I forgot to add fans, but I need to get them somewhere else as provider does not list them on items on sale.

I have also requested him for a PSU with less Watts and for a screw less case to feel more comfortable.

My brother might also change his dedicated GPU, which is a Nvidia 6600GT and will give it to me cost free. It has 256 MB dedicated memory. How good is the GPU on APUs?

Any advice on power saving options? I'll be getting higher bills in the future if it is on 24/7. I know about "green" HDDs.

---

### Post by ivotkl on 2013-01-11
Shameless bump. Anyone?

---

### Post by weryl on 2013-01-11
@drivemac: Shouldn't you create your own thread??

@ivotkl: Since you're talking about a headless server, I would drop the graphic card and use the integrated graphics for the initial setup. I really don't see why you'd want to waste money on it, unless you want to use a TV as the server monitor (to watch movies locally instead of streaming it). I wouldn't recommend it though, I wouldn't mix server stuff with everyday PC stuff.

It's also a bit hard to judge but that's a pretty huge amount of RAM unless you're planning on running several VMs. The way you describe it (media + remote access) doesn't point in that direction (IMO) and you could start with a single RAM bar initially and expend as needed.

My home server is 800MHz / 512M RAM, and runs minidlna (TV streaming), several forums, a blog (nginx), file sharing (samba, sftp, ftp), syncing and backup (dropbox, owncloud), downloads (rtorrent), monitoring (munin, webmin) and several custom services. And 512M is plenty for that. I actually had some trouble a few months ago with apache to serve my websites (the allocated memory was higher than 512M), but nginx allowed me to reduce it to <<512M.

---

### Post by JRV on 2013-01-11
My home server is built on an Atom mini-ITX board, 80 watt power supply, 2 gig RAM, and a 500 gigabyte hard drive.

It is a DHCP server for my home network, a network printer, downloads, and media streaming to my network.

It runs 24/7 so using low power saves on the electric bill.

---

### Post by weryl on 2013-01-11
My next server will be a Raspberry Pi :D

---

### Post by ivotkl on 2013-01-12
> **weryl said:**
> My next server will be a Raspberry Pi :D

Thank you all for the help.

@weril: I would get a Raspberry Pi if I knew its exact cost before confirming purchase. I have imported items limitations and foreign currency purchase limited to trips only, so I wouldn't know if it goes past customs. I agree with you with not mixing server / media purposes. I would like to eventually connect PC to a 1080p HDTV someday. Any recommendations on hardware, cooling and videocard? (Last two if really needed, I would like to save as much as I can).

---

### Post by Yellow Pasque on 2013-01-12
Does your supplier have a website so we can see your options?

---

### Post by ivotkl on 2013-01-12
Thank you for your reply (on both posts, hehe). You can take a look at website [here](http://www.pc-retail.com.ar/index.php?osCsid=mbkilmvq4464dqbs6j30h0df20).

However, he sends me an excel with updates almost every day and I can always ask him about a product in case he can get it. Find updated yesterday's Excel.

**_EDIT FOR JRV:_** Which are your full specs? How do I get those items? I've seen VIA mini ATX website, but I'm not too confindent about them. Any other option?

---

### Post by JRV on 2013-01-13
Motherboard: [http://ark.intel.com/products/42491/Intel-Desktop-Board-D945GCLF2](http://ark.intel.com/products/42491/Intel-Desktop-Board-D945GCLF2)

Power supply: [http://www.mini-box.com/picoPSU-80-60W-power-kit](http://www.mini-box.com/picoPSU-80-60W-power-kit)

Intel Atom motherboards are better and cheaper than VIA.
The board I used is no longer available but current Atom motherboards will work.

Two gig ram, and a 500 gig hard drive.

On a server the only specs that are important are the ethernet speed, gigabit, and the storage capacity.
Choose components to keep power consumption, and price, low.

---

