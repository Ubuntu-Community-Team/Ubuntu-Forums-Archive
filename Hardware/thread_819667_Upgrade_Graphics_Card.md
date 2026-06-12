---
title: "Upgrade Graphics Card"
date: 2008-06-05
forum: Hardware
---

### Post by Maratonda on 2008-06-05
What can I buy?

> 
Base Board Information
	Manufacturer: Acer
	Product Name: E61ML       
	Version:  
	Serial Number: 

System Slot Information
	Designation: PCI0
	Type: 32-bit PCI
	Current Usage: Available
	Length: Long
	ID: 1
	Characteristics:
		5.0 V is provided
		PME signal is supported

Handle 0x0014, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI1
	Type: 32-bit PCI
	Current Usage: In Use
	Length: Long
	ID: 2
	Characteristics:
		5.0 V is provided
		PME signal is supported

Handle 0x0015, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI2
	Type: 32-bit PCI
	Current Usage: In Use
	Length: Long
	ID: 3
	Characteristics:
		5.0 V is provided
		PME signal is supported

Handle 0x0016, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI3
	Type: 32-bit PCI
	Current Usage: In Use
	Length: Long
	ID: 4
	Characteristics:
		5.0 V is provided
		PME signal is supported

Handle 0x0017, DMI type 9, 13 bytes
System Slot Information
	Designation: AGP
	Type: 32-bit AGP
	Current Usage: Available
	Length: Long
	ID: 8
	Characteristics:
		5.0 V is provided


---

### Post by stchman on 2008-06-05
> **Maratonda said:**
> What can I buy?

Being an AGP board your choices are fairly limited.  You could go for an older Nvidia 5xxx series of card.

---

### Post by starcannon on 2008-06-05
Nvidia 6600gt or 6800gt/ultra would rock that machine. I don't know how many and of what quality there were of the 7xxx series nvidia agp cards.

Nvidia is the best bet though for maximum performance and compatibility in linux, at least for now, ATi is trying to make a comeback, and I do hope they pull it off, I like good competition.

New and Used 6600gt's
[http://search.ebay.com/search/search.dll?sofocus=bs&sbrftog=1&dfsp=32&from=R40&satitle=6600gt+agp&sacat=-1%26catref%3DC6&sargn=-1%26saslc%3D2&sadis=200&fpos=ZIP%2FPostal&sabfmts=1&saobfmts=insif&ftrt=1&ftrv=1&saprclo=&saprchi=&fsop=32%26fsoo%3D2&fgtp=](http://search.ebay.com/search/search.dll?sofocus=bs&sbrftog=1&dfsp=32&from=R40&satitle=6600gt+agp&sacat=-1%26catref%3DC6&sargn=-1%26saslc%3D2&sadis=200&fpos=ZIP%2FPostal&sabfmts=1&saobfmts=insif&ftrt=1&ftrv=1&saprclo=&saprchi=&fsop=32%26fsoo%3D2&fgtp=)

6800gt's
[http://search.ebay.com/search/search.dll?sofocus=bs&sbrftog=1&dfsp=32&catref=C6&from=R40&satitle=6800gt+agp&sacat=-1%26catref%3DC6&sargn=-1%26saslc%3D2&sadis=200&fpos=ZIP%2FPostal&sabfmts=1&saobfmts=insif&ftrt=1&ftrv=1&saprclo=&saprchi=&fsop=32%26fsoo%3D2](http://search.ebay.com/search/search.dll?sofocus=bs&sbrftog=1&dfsp=32&catref=C6&from=R40&satitle=6800gt+agp&sacat=-1%26catref%3DC6&sargn=-1%26saslc%3D2&sadis=200&fpos=ZIP%2FPostal&sabfmts=1&saobfmts=insif&ftrt=1&ftrv=1&saprclo=&saprchi=&fsop=32%26fsoo%3D2)

And finally in my opinion the Mac Daddy of agp:

6800 ultra's

[http://search.ebay.com/search/search.dll?sofocus=bs&sbrftog=1&dfsp=32&catref=C6&from=R40&satitle=6800+ultra+agp&sacat=-1%26catref%3DC6&sargn=-1%26saslc%3D2&sadis=200&fpos=ZIP%2FPostal&sabfmts=1&saobfmts=insif&ftrt=1&ftrv=1&saprclo=&saprchi=&fsop=32%26fsoo%3D2](http://search.ebay.com/search/search.dll?sofocus=bs&sbrftog=1&dfsp=32&catref=C6&from=R40&satitle=6800+ultra+agp&sacat=-1%26catref%3DC6&sargn=-1%26saslc%3D2&sadis=200&fpos=ZIP%2FPostal&sabfmts=1&saobfmts=insif&ftrt=1&ftrv=1&saprclo=&saprchi=&fsop=32%26fsoo%3D2)

Enjoy and happy hunting.

P.S. My top pick if I were going to drop a c note on an AGP card would be:
[http://cgi.ebay.com/nVidia-6800-Ultra-AGP-8x-256MB-DDR3-DVI-x2-6800Ultra_W0QQitemZ330241873082QQihZ014QQcategoryZ3762QQrdZ1QQssPageNameZWD2VQQcmdZViewItemQQ_trksidZp1638Q2em122](http://cgi.ebay.com/nVidia-6800-Ultra-AGP-8x-256MB-DDR3-DVI-x2-6800Ultra_W0QQitemZ330241873082QQihZ014QQcategoryZ3762QQrdZ1QQssPageNameZWD2VQQcmdZViewItemQQ_trksidZp1638Q2em122)
I never met a BFG card I didn't like.

okies thats all :) I promise :)

---

### Post by Maratonda on 2008-06-06
Thanks! I will take a look :)

---

### Post by Maratonda on 2008-06-11
So I bought a nvidia 6800 ultra, and it doesn't work with ubuntu. Damn.

---

### Post by sdennie on 2008-06-11
That card should work just fine.  What do you mean by "doesn't work"?  Have you gone to System->Administration->Hardware Drivers and downloaded the nvidia proprietary driver?

---

### Post by Maratonda on 2008-06-12
I have this problem:
[http://ubuntuforums.org/showthread.php?t=679366](http://ubuntuforums.org/showthread.php?t=679366)
I had to go back to my ATI to have a stable system, as I have work to do for  the university.
I had no direct rendering, no effects, tried envy, tried the official ones, but no luck.
I think that could be a problem from the switch, or the nvidia proprietary, nvidia open source, or ati open source drivers conflicting.

---

### Post by markharding557 on 2008-06-12
try installing drivers with envy or my favoured method of using the nvidia installer.
also it is wise to remove other drivers first

---

