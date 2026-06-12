---
title: "4Gb SD Card PC133, can work?"
date: 2006-09-19
forum: Hardware &amp; Laptops
---

### Post by joselin on 2006-09-19
Anyone knows is there is a way to let my sd card work on ubuntu?

Thanks

---

### Post by MichaelLehner on 2006-09-20
perhaps you could provide a few more information, because i don't think that here are many users here, who got to this place to play a quiz.

---

### Post by joselin on 2006-09-20
> **MichaelLehner said:**
> perhaps you could provide a few more information, because i don't think that here are many users here, who got to this place to play a quiz.

Well, SC cards >= 512 Mb can't be read on my computer, this is because a kernel limitation. What i wanted to know is if there is a fix or a pach or something like that to avoid this complaint.

Regards.

---

### Post by MichaelLehner on 2006-09-20
ah, ok, that means, that sd-cards work, but not this one you want to use. Where did you find about the kernel limitation that causes sd-cards greater than 512MB not to work? I'm not able to test this in the moment, but I tried to find in the internet and there was only information about cards 8GB+ that won't be supported in the moment, 2GB should work.

Have you tried only this card? I had a Problem with a 2GB card in my mobile, it worked in the pc, but i wasn't able to access it with my mobile, i also thought, that there is a limitation, but after several tests i sent it back and they found out, that the card wasn't ok. I got a new one, also with 2GB and this one now works in pc and mobile. I mean, you should not only test your card in another workstation, but test another card with 2GB in yours.

---

### Post by Rhubarb on 2006-09-20
If it's of any help, my 2GB SD card works fine in Ubuntu Dapper, straight from the default install up to the latest updates.  No problems at all.

For some of the newer 4GB upwards SD cards you will run into some problems.  For starters they all use fat32 (which shouldn't be a problem with Ubuntu).  There are some other imcompatibilities there too.
Check out the new **SDHC** 4GB card:
[http://www.sandisk.com/Products/Item(1982)-SDSDBR-4096-SanDisk_Standard_SDHC_Card_4GB.aspx](http://www.sandisk.com/Products/Item(1982)-SDSDBR-4096-SanDisk_Standard_SDHC_Card_4GB.aspx)
You'll need a compatible SDHC reader to read any SDHC 4GB+ cards.

If you're having problems with your plain normal SD card, say a 2GB card, then the solution is to try a different brand (sometimes a bad batch can be made, as Michael has said above).
I know from experience that some brands just won't work with some types of card readers.

It seems all the problems you are having are purely hardware related, nothing to do with software or the kernels that you are using (Well maybe, you might need a kernel update that supports SDHC card readers if you wish to use a card 4GB+)

---

### Post by joselin on 2006-09-20
I saw it in [http://marc.theaimsgroup.com/?l=linux-kernel&m=114980773206129&w=2](http://marc.theaimsgroup.com/?l=linux-kernel&m=114980773206129&w=2)

My card reader is able to read the card in other OS.

And try another brand is not an option for me now.

---

### Post by Rhubarb on 2006-09-25
Hmmm, that's a bit odd.
I don't know enough about recompiling / patching kernels to fix this for you.
If you know anyone with an SD card > 512MB or has an SD card reader, see if you can borrow it off them to test on your Ubuntu system.
Something is very weird here, as stated before, I have no problems with my SD card reader and my 2GB card.
As there's no drivers for my internal card reader in my laptop yet, so I'm using a regular cheap usb SD card reader.

Edit: I have a feeling that Linux currently has no SDHC drivers at the moment.  As you have a 4GB SD card, it MUST be SDHC.
I don't know what "PC133" has to do with a 4GB SD card.  - PC133 is just the speed (133MHz) of SD **RAM**, which is completely different to your SD card.

---

### Post by punong_bisyonaryo on 2008-01-07
> **Rhubarb said:**
> Edit: I have a feeling that Linux currently has no SDHC drivers at the moment.  As you have a 4GB SD card, it MUST be SDHC.

Do you know if SDHC cards are supported as of Gutsy?

---

### Post by Neobuntu on 2008-01-22
OK guys, I have a new Adata 4GB Micro SDHC drive.

The Alcor > 058f:6331 Alcor Micro Corp. via lsusb) reader that I have now, is reported to work with SDHC. It does not work.

I have heard Adata cards come dead or go out within minutes. While this is certainly possible. It's more likely an incompatibility.

I have **not** been able to read or format my (above) flash drive with Either XP Pro updated (and hot fixed) nor Kubuntu (Two computers) 7.10 Gusty. 

I can not BELIEVE the poo I had to go through with Microsoft. Including begging by email to get a hot fix for my (Already fully, CUMBERSOME and TIME WASTING to update) XP pro (for testing only).

XP was with painful waits to try and get to a format screen and in the end it will not read(or write a format). I can't be sure it needs formating. I would expect it to be already formated but who knows?

I guess it is either NOT a **match** to this reader (new one comming soon) or still needs software driver help. Lastly, it might be a bad flash drive.

HELP!

P.S. I do have an SD adapter that came with but I seriously doubt my old half broken printer with SD reader (or old camera) will read SDHC.

The only hope is the SD adapter (from MicroSd) handles the SDHC stuff. I'm guessing not. Anyone know about that?

Beside help and information needed, I post this to state my guess, that it is NOT so much an SDHC reader that is needed but a matched "SDHC capable" reader and the right drivers/modules. What say you?

---

### Post by Neobuntu on 2008-01-22
Well the MicroSDHC card to it's SD adapter did **NOT** allow it to work in my old camera (as you would expect).

I'm still wondering why the reader I have now was reported to work with SDHC but does not with this Adata MicroSDHC. 

I could try the full SD (no mention of HC on this included SD adapter) with the turbo SDHC Micro inside in my old printer with it's SD slot but it broken and not likely.

So I wait for my next SDHC rated micro reader; to see if it's compatible. It **should** be.

Still, why not the Alcor?

So I guess I'm asking, does **ANY** SDHC **micro** reader work with **ANY** MicroSD**HC**?

---

### Post by Neobuntu on 2008-01-23
**Micro** **S**ecure **D**igital **H**igh **C**apacity

Said another way, do USB MicroSD readers/adapters not only require SDHC capability (for adapting SDHC cards) BUT ALSO be matched in some manner to a certain model (USB reader to card combo) as well?

BTW the jury is out on whether "Class 6" truly means faster.

Big humongous 4GB drive! Itty bitty living space (Pinky figernail size).:)

---

### Post by Neobuntu on 2008-01-24
I have now found information stating that my **EXACT** Alcor Micro USB reader (6331) is slow and not SDHC compatible.

---

