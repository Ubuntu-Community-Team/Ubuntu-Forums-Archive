---
title: "I haven't been able to find complete compatibility info..."
date: 2014-07-17
forum: Hardware
---

### Post by ddmcp2000 on 2014-07-17
I'm sick of Windows.  Ransomware this.  Malware that.  With what my wife and kids do, Ubuntu will be perfect.  I'm always afraid that I'm going to come home to a melted down Windows OS...

Anyway.  I have an i7-960 on an eVGA X58-SLi3 Motherboard with 24GB of RAM.  An eVGA GTX560Ti graphics card drives an Acer 26" LCD on the HDMI output.  I have a RevoDrive2 240GB PCIe hard drive for my boot partition.  There is a RAID card in there, (forgotten brand, but it's an expendy one, and I believe it's a full hardware RAID solution.  RocketRAID, I think...  If not, it's a Dell PERC6 or H310) with four 1TB Seagate drives in a stripe, it was for games and swap file, when I was a gamer, but now it stores files like movies (full-res DVD rips - no compression) and music (mostly M4A and FLAC, some WAV, and a few MP3).  I have an iPod Classic 160GB, that I really don't want to lose support for, as my car's stereo system is built like my PC - "when too much is a good start" - very high res, and I cannot STAND the sound of MP3s, so WAV or M4A (Apple Lossless).  There's a dedicated USB3 card in place, as well.

The big question I am having at this time, as I am fairly certain all of the rest of the hardware will work, is this:  What's support like for the RevoDrive2, now?  I realize it's a FakeRAID device, and I know that I can turn off the RAID function is the card's BIOS, and present two 120GB SSDs to the OS, but I'd just as soon keep the 240GB as a single partition.  How tough is this to do, and if it can be done, what's the stability like?  I've been leery of installing on a FakeRAID in the past, but I'm ready to throw Windows out, completely.

The other small question is this:  What's the nVidia support like now?

I also know that the OpenOffice is different, but it still offers reasonably full backward compatibility support for MisroSquish's Office documents?

---

### Post by LastDino on 2014-07-17
I wont comment about the RAID but nVidia compatibility sort of depends. Some people have better experience with open source drivers and some with proprietary ones. It is also observed that generally cards with little older release date have better chance of working flawlessly than brand new ones sometimes do. Nevertheless, you can rest assured that there are plenty of people here willing to help if you run into any trouble with them.

Backward office compatibility with MS is something you need to decide yourself, I've foundLibreOffice to be sufficient for my needs and I didn't have any problems moving/editing documents from Windows to Linux machines.

---

### Post by ddmcp2000 on 2014-07-20
Thank you for that input, LastDino!  I'll certainly keep the nVidia driver think in mind as I move forward.

I've seen LibreOffice generally does a fine job translating Office documents, and even offers native PDF exports.  Again, thanks for your time and input...

Anybody have any comment on the RAID thing?  Like I said, that's my big stumbling block right now...

---

### Post by MartyBuntu on 2014-07-20
> **ddmcp2000 said:**
> 

Anybody have any comment on the RAID thing?

Do you really need RAID?

---

### Post by ddmcp2000 on 2014-07-21
Need?  Well, no.  It's a want, I admit.  But as I described in my opening, I have a RevoDrive X2; which is two 120GB SSDs in a RAID for logically configured 240GB partition.  Also as I mentioned, I *can* break the RAID, and run a single 120GB partition, (and these two 120GB physical drives are seen by Ubuntu, natively) but why should I have to do that?  I'm ready to dump Windows altogether.  It was a really expensive device when I bought it, and I really do NOT want to have to get rid of it, or use it in a "crippled" state.

---

### Post by Mark Phelps on 2014-07-21
> it still offers reasonably full backward compatibility support for MisroSquish's Office documents? 

I'm NOT bashing LiverOffice or OpenOffice  -- but the newer "XML" format MS Word documents can present some formatting problems when opened in anything other than MS Word, and the newer the originating Office versions, the worse the problems.

A very simple Word document (just a buch of text with paragraphs) is likely to work OK, problem is, with recent Office versions, folks can embed lots of different stuff into Word documents.  This creates formatting problems with non-MS apps, and the more complex the embedding is, the greater the problems.

Nothing offers FULL compatibility with MS Office documents other than MS Office.  Sorry, but that's the "inconvenient truth"!

---

