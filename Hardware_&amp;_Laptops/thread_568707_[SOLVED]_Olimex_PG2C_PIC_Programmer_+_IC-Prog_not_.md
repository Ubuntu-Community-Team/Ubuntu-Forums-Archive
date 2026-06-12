---
title: "[SOLVED] Olimex PG2C PIC Programmer + IC-Prog not working"
date: 2007-10-06
forum: Hardware &amp; Laptops
---

### Post by gfixler on 2007-10-06
I'm on a ShuttleX PC, trying to get IC-Prog in Wine 0.9.46 to program a PIC16F84A over a serial line. I've done this before on my previous Shuttle - and it worked great - but this new PC is 2 versions of Ubuntu ahead (Dapper vs. Feisty), Wine is several versions ahead, and I haven't tried to do this for about a year, or two. First some local info...

```
$ dmesg | grep tty
[   25.815248] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.815893] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
```

```
$ setserial -g /dev/ttyS[01]
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3
```

This seems to say (to me, a n00b) that at least ttyS0 is working right. The 00:07 and "unknown" bits make me skeptical about ttyS1. I couldn't glean any useful info with quite a bit of searching pieces of these lines in Google.

I don't have any other serial devices to test out here, and I searched and searched for a way to detect my PG2C, to no avail. The serial ports don't seem to have a way to list what's connected, as with USB ports, which makes sense - they're just TX/RX lines. Please correct me if I'm wrong, and there is a way to see my device.

As for Wine, I've set IC-Prog up to use the Windows 98 setting. WineHQ says to set up the com ports thusly:

```
ln -s /dev/ttyS0 com1
```

Mine are already set up that way:

```
~/.wine/dosdevices$ ls -la | grep tty
lrwxrwxrwx 1 gfixler gfixler   10 2006-10-10 23:29 com1 -> /dev/ttyS0
lrwxrwxrwx 1 gfixler gfixler   10 2006-10-10 23:29 com2 -> /dev/ttyS1
```

In IC-Prog, I've tried reading, writing, erasing, and verifying. I've spent the night getting errors, and finally have it to a point where it does all of these operations, and verifies things as correct, but it does this for both serial ports in the Hardware options, and even if I flip the PIC chip around backwards! I know I ran into this exact same problem years ago, but can't remember at all how I fixed it. I'm pretty positive it had to do with setting up the links from comN to ttyS[n-1]. I've also tried another, identical chip - same results. It's like it's just telling me what I want to hear :)

I've also tried picprog from the repos:

```
$ picprog -p /dev/ttyS0 --erase -q
/dev/ttyS0:PIC programmer missing or chip fault
/dev/ttyS0:2006:unable to read pic device id
```

```
$ picprog -p /dev/ttyS1 --erase -q
Unable to set RTS/DTR on tty /dev/ttyS1:Input/output error
```

Yes, I tried both. I keep trying both with everything, because I have no idea what port my lone serial connection in the back thinks it is. Is there a way to check it? I just can't seem to find anything on that. My Google-fu is weak.

So far I have seen nothing at all happen for hours of trying. The little red light on the PG2C hasn't lit up at all. I would love any info that could move me forward on this. I have Halloweengineering to get done ASAP.

Thanks!

---

### Post by gfixler on 2007-10-06
Posting back what I did here, as it's solved.

Just after posting, I decided to try a different RS-232 cable, and found the cable wasn't plugged into the computer! I know it had been, because I pulled the desk out from the wall, and plugged it in. It must have fallen out at some point. I pushed it back in, and tightened the screws. I went through all the tests again, to no avail.

I decided to reboot into XP, and downloaded IC-Prog in there, while Windows popped up tons of announcements, installed automatic updates I didn't want, and just generally got in my way :)  I'm never in there, and tend to just use it as a last resort when nothing in Linux works, especially with some odd hardware - just to see if it's OS-specific. Nothing worked there, either. All the same tess were doing nothing still, though my only option now was Com 1, as listed in the Hardware section, so at least I narrowed down which port the plug on the back is considered.

Then I remembered I have a nice multimeter, so I unplugged the PG2C, looked up the pinouts, and tried with test clips to check for proper DC voltages, but they were all screwy. I kept getting -OL, which I think means 'overload.' I played with the range, reversed the leads, checked the battery by unscrewing the back, and did a lot of IC-Prog tests to get them to say something (e.g., when clicking "enable data out") but nothing would change.

I tested a 9V with the multimeter, but the values were way too high. I tested a D battery, and for the first time I got something close - 1.5 to 1.6VDC. It seemed high, but at least it was in the ballpark. Then I tried the 9V, and it was saying 5.6VDC - that's more like it. It was a really weak, old battery. Another similarly old 9V gave a similar result.

I went back and tested the TX line, but got nothing. I looked up how to make a loopback, which was cake - I just took off the test clips, and ran one test clip from pin 2 to pin 3, and then fired up HyperTerminal, set a few options the specified way, and typed letters, which were echoed back to me - each press generated 2 of that letter. It was looping back. Removing the connection, it wouldn't do that.

I connected the multimeter via the test clips to the cable again (TX and ground), and tried writing the chip - something I'd done exactly the same way earlier with no results - and this time, the voltages danced around - a result! I hooked the PG2C back up, and its red light finally came on when performing the various chip operations through IC-Prog! I was able to write a sample hex file I found online to the chip, close out entirely, go back in, and read the same info back from the chip. Awesome. I went through the Hardware settings to remember them for tests back in Feisty: Programmer=JDM Programmer, Ports=Com 1, I/O Delay=20 (10 was too fast, LED barely lighting, and verifies failing, but 20 works great), Interface=Windows API, Communication=nothing checked (nothing inverted).

Back in Feisty, I set it up the same way, making sure Wine launched the program in Windows '98 compatibility mode (others give 'privileged instruction' errors). It worked! I'm still not sure what was going on with that port, or even briefly with the multimeter, but it was likely my fault Electronics confuses me. I have a workbench across the room, with pegboard fixed to the back (above the bench, so I can use it while working), in which I've sunk a custom electrical outlet with an RS-232 port on it, so I can work on serial projects over there. I ran the 3 interconnected cables from the PC to that, and pushed the PG2C into the plate, and it could still read/write/verify over there, so I'm back!

---

