---
title: "[SOLVED] HP Deskjet 930C Won't Print. &amp;quot;Not Connected&amp;quot;"
date: 2008-04-14
forum: Hardware &amp; Laptops
---

### Post by Literati on 2008-04-14
Hi everyone,

I'm trying to print a document but when I click print it says "Not Connected?" and won't print. 
Nothing in my setup has changed since the last time I was able to print, so I really don't know what's wrong.

My hunch is this...

Device URI: hp:/par/DESKJET_930C?device=/dev/parport0 

I think that might be wrong, ad I checked, and there is no directory called /dev/parport0
But I wouldn't know what to change it to, or how to fix it.

Can someone please help me print? :)

---

### Post by Literati on 2008-04-14
Here's the output of 

sudo tail -f /var/sys/syslog

18:15:36 Matt parport0: io/hpmud/pp.c 786: unable to open hp:/par/DESKJET_930C?device=/dev/parport0: No such file or directory 
Apr 14 18:15:36 Matt parport0: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Apr 14 18:15:36 Matt parport0: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds... 
Apr 14 18:16:06 Matt parport0: io/hpmud/pp.c 786: unable to open hp:/par/DESKJET_930C?device=/dev/parport0: No such file or directory 
Apr 14 18:16:06 Matt parport0: prnt/backend/hp.c 496: unable to connect hpssd socket 2207: Connection refused 
Apr 14 18:16:06 Matt parport0: prnt/backend/hp.c 625: INFO: open device failed; will retry in 30 seconds...

---

### Post by Aearenda on 2008-04-14
Some ideas...
1) Has someone changed any BIOS settings, such as the one about disabling the parallel port?
2) Mice been chewing your cable? :-) Try changing it.
3) Is there a good reason not to use USB? I have my 930 attached by USB.
4) Has CUPS detected the printer by a different name? See what is detected if you go to [http://localhost:631](http://localhost:631) and go as if to add a new printer (depending on which version of Ubuntu you have)

---

### Post by Literati on 2008-04-14
1) I'll check the BIOS, but I have an old MOBO, so I doubt there are any settings like that in it anyway. I'l report back.
2) Definitely not, it's suspended in the air
3) I could... But call me dense, but I don't see a USB port. 
4) Nope, it's still detected as "Deskjet" as it should.

Thanks for the preliminary assessment! :)

---

### Post by Aearenda on 2008-04-14
Mice with wings? After all, if pigs can fly...

The USB port on my 930C is just next to the parallel port, to the right when viewed from the back. Maybe there was an earlier version without USB?

Unless it's the BIOS, my next test would be to plug the printer in to a different PC to see what happens.

---

### Post by Literati on 2008-04-15
In the BIOS, it does say "Parallel Port : Disconnected"

When I go to switch it, I'm given what can only be decribed as a plethora of options, can you make sense of what I should do?

First Choice: 378 - 278 - 3BC
Second Choice: Parrallel Port Monitor (IIRC): Normal - Bidimensional - EPP - ECP
Third Choice - IRQ 5 - IRQ 7

God knows what I should coose 
(Or should I say, His Noodlyness knows)

---

### Post by Literati on 2008-04-15
:(
Does anyone know what to set it to?

---

### Post by Aearenda on 2008-04-15
I would set I/O address 378 for the first one, and IRQ 7 for the third unless you have more than one parallel port or a lot of older addon hardware. IRQ 5 is probably ok too. You may have to reserve whichever you choose of 5 or 7 in the PCI/ISA interrupt config page. 

The second setting will probably work regardless but I would start testing with it set to ECP, then EPP, then bidirectional, and lastly normal.

Actually, I don't think there are any spaghetti monsters involved here, fortunately! :-)

EDIT: I was typing this when you posted your last question!

---

### Post by Literati on 2008-04-15
Thank you for the reply :) 

I'll test these out momentarily and report back.

In the meantime, if you have the time, I would like to actually LEARN what I'm telling my BIOS/coputer to do. 
What do these settings even mean / determine?
I mean, it's great that I'll (hopefully) be able to fix this for myself, but if I can help out others in the future too, that'd be even better :)

Thanks again!

---

### Post by Literati on 2008-04-15
SUCCESS!
It worked! (or seems to have, as my document printed :P) 
Let's hope re-setting it up in Hardy when the stable comes out doesn't kill me all over again :P

Thank you so much for your patience and help.
I'd still be curiosu as to the answer to my last question though. I'd love to understand what I've done. :)

---

### Post by Aearenda on 2008-04-15
Congratulations!

What you did was to tell the BIOS to remember how to configure the parallel port. (Of course, the question is - why did it forget?)

The BIOS is independent of the operating system - so installing Hardy shouldn't make it forget again.

From the earliest days of IBM-compatible PCs, hardware has had an input-output (I/O, as distinct from memory) address range, where the 'registers' the CPU uses to 'talk' to the hardware can be found, and an Interrupt ReQuest line (IRQ) which is used to attract the CPU's attention when the hardware needs it, interrupting what the CPU was doing. The 'standard' settings for a parallel port are IRQ 7 (I think - my memory is getting hazy) and IO address 378. 

There are similar settings for the serial ports COM1 and COM2, as well as for network cards and so on. Modern PCs just do all this stuff automatically.

The other setting (normal/bidi/ECP/EPP) governs how clever the parallel port should be, and it evolved over time as printers (in particular) got smarter - so they could do things like report ink levels etc instead of just blindly printing even when there is no ink.

Google just suggested this for more info: [http://www.karbosguide.com/books/pcarchitecture/chapter40.htm](http://www.karbosguide.com/books/pcarchitecture/chapter40.htm) (or [http://www.karbosguide.com/books/pcarchitecture/start.htm](http://www.karbosguide.com/books/pcarchitecture/start.htm) for the whole thing). It looks a bit too detailed, but it might help.

I'm glad it worked in the end!

---

### Post by Literati on 2008-04-16
Well, the good thing is that I more or less understand what's happening.
Thank you for providing both a layman, and technical explanation :) I'm glad I had both and will definitely read more at that link you rprovided. Granted, I'm only 17 and might not have the time to do so in the coming week or two, but I will for sure get around to it :)

Thank you very much for all the help Aerenda, it was very clear and helpful :)

---

### Post by Aearenda on 2008-04-16
Happy to help - that article is a bit dated, but then so is the parallel port!

---

