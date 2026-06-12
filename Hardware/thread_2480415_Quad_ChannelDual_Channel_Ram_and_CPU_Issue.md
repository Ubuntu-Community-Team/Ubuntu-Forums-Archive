---
title: "Quad Channel/Dual Channel Ram and CPU Issue"
date: 2022-10-29
forum: Hardware
---

### Post by caseydwilder on 2022-10-29
I have an Intel i7 4790k CPU and the Intel spec sheet suggests that the CPU is Dual Channel. 

My Motherboard (Asrock 97 something Extreme+) has four RAM slots. 

I have 4 sticks of 8gb RAM (disclaimer on this shortly).

I just put the second two sticks in because I was getting awful close to my RAM max regularly. I've noticed, however, now when I get over the old limit (low 15gb range), the computer becomes almost entirely unresponsive until I get my RAM usage down below the two stick limit. 

I don't know anything about any of this, so I'm sorry if this sounds goofy, but is there any work around to somehow trick Linux into treating my four sticks as two sticks (or a quad channel as a dual channel, etc). 

Basically, I want to keep my four sticks in and make this arrangement work ideally if there's a software/terminal based solution I can implement. 

Disclaimer about the RAM: It's actually two different clock speeds of DDR3. I originally didn't use the other sticks for that reason because I heard it's not ideal. However, I read online that the faster would downclock. I checked my motherboard and it does indeed register it as the slower clock of the two. Linux says it, too, though I'm sure it's reading it right off what the BIOS is spitting at it. I originally thought that this was my issue, and while researching it, I noticed the dual channel/quad channel issue and sure enough, my CPU, as glorious as it's been over the years, is simply not suited to run four sticks. So, I've decided to discredit the clock speed issue and focus in on the channel issue. 

Thanks in advance, homies. <3 You guys are always so savvy with this stuff.

---

### Post by Autodave on 2022-10-29
Mixing different RAM sticks is normally not a good idea.  Sometimes it works, often times it doesn't.  IF I were going to try it at all, I would put the lesser (slower) RAM in the first 2 slots and the faster in the latter two slots.  If that doesn't work it is time to but 4 sticks that match.

If your motherboard supports quad channel memory, then the 4 sticks have to be matched.

---

### Post by caseydwilder on 2022-10-30
Thanks for the reply, Dave. I appreciate your insight and I'll check the slots I have the ram in to be sure of their configuration. 

I noticed you didn't say anything about the dual channel CPU I have. Is that not an issue at all? Again, I've got no expertise in this specific area. 

Thanks again.

---

### Post by Autodave on 2022-10-30
Not sure what you are asking about that.  Are you asking as per the dual channel RAM chips?  If so, you can still try moving the slower ones to slots 1 & 2 and trying.  Will it work?  Maybe, but probably not.  But all it will take for you to find out is a couple minutes of your time.

I am assuming that all of your RAM chips are dual channel.  If not, it will definitely not work.

---

### Post by caseydwilder on 2022-10-31
Thanks again, Dave. 

My CPU says that it only supports dual channel, so I'm assuming that means the CPU itself cannot support 4 sticks of ram? 

The brand on the ram, I don't remember, but it is a bit older, but higher end gaming RAM (red metal and decorated and such), so I'm sure the ram itself is probably fine. I will surely try swapping the sticks of ram around and I'll try to dig up the manual for the motherboard to see if there's anything I need to know about it. 

Again, appreciate your help.

---

### Post by Yellow Pasque on 2022-10-31
> **caseydwilder said:**
> My CPU says that it only supports dual channel, so I'm assuming that means the CPU itself cannot support 4 sticks of ram?

No. Four sticks can be used in dual-channel mode (2x2), but if they're unmatched, things might get complicated. Please give output of:
```
sudo dmidecode -t memory -t baseboard
```

EDIT: Also note that different motherboards use different physical layouts for dual-channel operation (i.e some mobos group slots 1 and 3 as a channel, and others group slots 1 and 2). We wouldn't things to be too easy, would we? ;p

---

### Post by caseydwilder on 2022-11-01
I see that there were some errors. I was more successful checking cpu-x instead. I will send that, too. 


```
# dmidecode 3.2
Getting SMBIOS data from sysfs.
SMBIOS 2.8 present.


Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: ASRock
	Product Name: Z97 Extreme6
	Version:                       
	Serial Number: M80-63022100075
	Asset Tag:                       
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis:                       
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0


Handle 0x000E, DMI type 16, 23 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 32 GB
	Error Information Handle: Not Provided
	Number Of Devices: 4


Handle 0x0013, DMI type 17, 40 bytes
Memory Device
	Array Handle: 0x000E
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 8192 MB
	Form Factor: DIMM
	Set: None
	Locator: ChannelA-DIMM0
	Bank Locator: BANK 0
	Type: DDR3
	Type Detail: Synchronous
	Speed: 1333 MT/s
	Manufacturer: 0420
	Serial Number: 00000000
	Asset Tag: 9876543210
	Part Number: F3-2400C10-8GTX   
	Rank: 2
	Configured Memory Speed: 1333 MT/s
	Minimum Voltage: Unknown
	Maximum Voltage: Unknown
	Configured Voltage: Unknown


Handle 0x0015, DMI type 17, 40 bytes
Memory Device
	Array Handle: 0x000E
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 8192 MB
	Form Factor: DIMM
	Set: None
	Locator: ChannelA-DIMM1
	Bank Locator: BANK 1
	Type: DDR3
	Type Detail: Synchronous
	Speed: 1333 MT/s
	Manufacturer: 0420
	Serial Number: 00000000
	Asset Tag: 9876543210
	Part Number: F3-2400C10-8GTX   
	Rank: 2
	Configured Memory Speed: 1333 MT/s
	Minimum Voltage: Unknown
	Maximum Voltage: Unknown
	Configured Voltage: Unknown


Handle 0x0017, DMI type 17, 40 bytes
Memory Device
	Array Handle: 0x000E
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 8192 MB
	Form Factor: DIMM
	Set: None
	Locator: ChannelB-DIMM0
	Bank Locator: BANK 2
	Type: DDR3
	Type Detail: Synchronous
	Speed: 1333 MT/s
	Manufacturer: 0420
	Serial Number: 00000000
	Asset Tag: 9876543210
	Part Number: F3-2400C10-8GTX   
	Rank: 2
	Configured Memory Speed: 1333 MT/s
	Minimum Voltage: Unknown
	Maximum Voltage: Unknown
	Configured Voltage: Unknown


Handle 0x0019, DMI type 17, 40 bytes
Memory Device
	Array Handle: 0x000E
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 8192 MB
	Form Factor: DIMM
	Set: None
	Locator: ChannelB-DIMM1
	Bank Locator: BANK 3
	Type: DDR3
	Type Detail: Synchronous
	Speed: 1333 MT/s
	Manufacturer: 0420
	Serial Number: 00000000
	Asset Tag: 9876543210
	Part Number: F3-2400C10-8GTX   
	Rank: 2
	Configured Memory Speed: 1333 MT/s
	Minimum Voltage: Unknown
	Maximum Voltage: Unknown
	Configured Voltage: Unknown
```

---

### Post by caseydwilder on 2022-11-01
[IMG]https://imgur.com/a/S3oFW84[/IMG][IMG]https://imgur.com/zec8HjM[/IMG]https://imgur.com/a/S3oFW84

Here is the output from CPU-X

---

### Post by caseydwilder on 2022-11-01
[https://www.newegg.com/g-skill-16gb-240-pin-ddr3-sdram/p/N82E16820231589?Item=N82E16820231589](https://www.newegg.com/g-skill-16gb-240-pin-ddr3-sdram/p/N82E16820231589?Item=N82E16820231589)
[https://www.newegg.com/g-skill-16gb-240-pin-ddr3-sdram/p/N82E16820231489?Item=N82E16820231489](https://www.newegg.com/g-skill-16gb-240-pin-ddr3-sdram/p/N82E16820231489?Item=N82E16820231489)

And according to my order history, I have G.Skill Ripjaws 1600 and G.Skill Trident 2400. Idk where the 1333 ram speed is coming from, but apparently I'm downclocked to it. I never paid attention to it before, so I don't know if my motherboard is doing it for some kind of compatibility reason or something.

---

### Post by Yellow Pasque on 2022-11-01
Well, from the mobo manual, it looks like you should put the Trident in slots 2 and 4, and the Ripjaws in slots 1 and 3. See how it works. 

BTW, the dmidecode output tells us that you have have 4  sticks with identical part numbers. This doesn't match up with what you told us. I'm confused.

---

### Post by caseydwilder on 2022-11-02
I'll go ahead and try that right now. Thanks for the assistance. 

And I noticed that. That's why I sent the rest of the information. I don't know if that's the mother board's doing (because I think they're all showing as identical there, too). I assumed it was some compatibility mode or something.

---

### Post by caseydwilder on 2022-11-02
Thanks for the quick reply. 

I opened the case and attempted to rearrange the sticks and found an interesting turn of events. It seems I've slightly misinformed you and maybe it's a different problem? And explains why you're confused ahaha (sorry)

Before adding the ram, I looked at what CPU-X said I had in the computer (to avoid taking it apart) and it said I had a 1333 speed pair of sticks. And I had the Trident physically in my hands, which were 2400. So, I immediately assumed it was a different speed. I had previously bought Ripjaws for a computer I built my parents (1600). It didn't make sense to me because I was certain I put the Ripjaws in their build (it's been like 5+ years), but since the computer was giving me a slower clock, I assumed that I accidentally put it into my own build at some point.

Point being, I've actually got four matching sticks of Trident 2400 in my build. All identical, 8gb each. 

When rebooting my computer, I checked my Asrock UEFI settings and it identified all four of my sticks as 1333 instead of 2400. So, I'm guessing it is downclocking them for some reason? So, the problem could potentially lie there. 

Regardless, the issue still persists:

Any time I exceed 16gbs of ram usage, the computer turns into an unusable slideshow, despite having 32gb of available RAM (BIOS successfully recognizes 32gb, also).

---

