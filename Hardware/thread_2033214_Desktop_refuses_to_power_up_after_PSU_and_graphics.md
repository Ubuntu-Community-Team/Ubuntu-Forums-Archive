---
title: "Desktop refuses to power up after PSU and graphics card upgrade"
date: 2012-07-25
forum: Hardware
---

### Post by Haggetti on 2012-07-25
Greetings.

I recently upgraded my custom build desktop, due to  it having a rubbish graphics card for gaming.

I upgraded it to a Radeon 6850 which would more suitable for gaming. After powering the rig, it made a disturbing whirring noise. I found out this was because my PSU was insufficient (450W) when I needed 550.

I replaced the PSU with a G7 Power extreme 780W. Now the Desktop refuses to power up. Occassionally a light comes up on the motherboard when I plug the power supply in. The fan on the heat sink also moves roting by one blade 

From what I can tell none of the components have broken or burnt out, and all the wires are plugged in. I have tested it with multiple in wires all of which work with other devices

So Does anyone have any idea what I've done wrong or missed?

**My build**

MSI 880GM - E41
G7 Power extreme 780W
Radeon 6850
2X4GB sticks of DDr3 RAM
Quad core CPU (unknown type)
1X 500GB HDD
1X 2TB HDD
1X 3TH HDD

An image of my desktop if this helps
[http://imageshack.us/photo/my-images/215/imag0092g.jpg/](http://imageshack.us/photo/my-images/215/imag0092g.jpg/)

---

### Post by QIII on 2012-07-25
Unplug the computer from the wall socket.  Take everything that is not soldered on out of the case, except PSU, the motherboard/cpu/hsf and the front panel wires.

Plug in the 24 and 8 pin mobo power cables plug the PSU into the wall and hit the power switch.  If you get the same behavior and no POST beeps, either your PSU or your mobo is defective.

That does not mean other components are not also damaged.

"Disturbing noises" rarely bode well.  If a PSU fails it may, depending on the nature of the failure, produce catastrophic damage to any component.

Neither does a light that "sometimes" comes on bode well.

---

### Post by Haggetti on 2012-07-25
OK I did as you said and got no response from the computer.
How will I know if it's the board or the PSU.

The noises came when I had the card in on a PSU with to little power I promtly shut it off and removed the PSU and replaced it. 
Considering this is the second PSU the first one I brought for the new card went, (High pitched noise and horrible smell.) I think I might have burned out the board

---

### Post by QIII on 2012-07-25
Computers run on blue smoke.  If you let too much out, they won't run.  ;)

I'm assuming you normally get at least the final POST beep under other circumstances:  i.e.: you have a mobo speaker?

Ok.  From what you describe about the first PSU, it failed catastrophically.  Unfortunately, depending on the mode of failure, you may have shot an over-volt or over-amp spike right through your motherboard.  That can damage connected components, but does not always.  If one is really lucky, the CPU is spared.

From what you are telling me about the "occasional" light and the fan, my guess is that a capacitor or two on the mobo blew out.  The caps store electricity to energize circuits as needed.  They blow, no flow.  Take the mobo out carefully.  Remove the CPU and HSF.  Go to a well lit spot and bring a flashlight and a magnifying glass.  I would be willing to bet you will find swollen or completely burned capacitors, gaps burned in traces, scorching on the PCB or even melted solder.  Look at both sides of the mobo and look carefully.  Smell the motherboard.  If it smells smokey anywhere, it's shot.

---

### Post by Haggetti on 2012-07-25
Ok, I extracted the motherboard.
Neither I nor my friend could see any damage to the capacitors
There is a faint smell but it is very hard to tell what it is.
I couldn't see any solder that has run on either side of the board.

Which means this is PSU no.3 blown. If you are correct about the original PSU.

---

### Post by Haggetti on 2012-07-25
Reguarding the beap. No I do not have a speaker on my mobo. there's a sound slot which is filled but I never recall it making a noise. It was running fine before I performed the upgrades

---

### Post by QIII on 2012-07-25
I doubt your newest PSU shot.  Does your friend have a spare mobo speaker you could plug in to the motherboard temporararily to see if you get a complete POST?  Most mobos have a chassis speaker header.  That's not the one you plug your font I/O panel in to.

As much as things cost, it's worth taking the time to be sure.

---

### Post by Haggetti on 2012-07-25
No, my friends have laptops so they can't help with that or testing the PSU.
The only Audio wire was the one connected to the front board. So I'm afraid that won't work

---

### Post by QIII on 2012-07-25
Check your mobo documentation or find it on line.  I would be very surprised if there is not a bare 4 pin header labeled "spkr" or similar somewhere on the board.

Again, if you just put a new PSU in and the machine would not run the first time you turned it on, it is unlikely to be the new PSU at fault.

---

### Post by ahallubuntu on 2012-07-25
A new power supply could most certainly be bad.  Where did you get it?  Even if brand new could be bad.  A certain small percentage of them are bad from the factory.  Read reviews on the electronics retailer websites sometimes; lots of people post that their new electronic components are completely bad, even if that represents only a small percent of actual buyers.

I assume you double-checked all the connections, that they are plugged in firmly?

Can you swap the old power supply (and old video card) back in?  Obviously installing a different power supply is one easy way to check whether the other one is bad or not.  Having a power supply tester (which you don't have) would be handy...

---

### Post by Haggetti on 2012-07-25
Not that I can see on the board or in the manual/
The only thing that matches this is a slot labled JAUD1 which was wired up and no sound was heard.
My first thought was that I missed a wire but,the only wire that wasn't wired in was "4pin floppy connector" and the spare 4pin power (which was for use if the board had an 8pin power)

---

### Post by Haggetti on 2012-07-25
@[ahallubuntu]("http://ubuntuforums.org/member.php?u=32392")

I tried placing the old PSU back in and I got no response.
I did double check all the connections, I even removed the front of the case to check the ones connected to the power button. As I said it is possible I have missed something, even though the only free ones are SATA power leads a 4pin floppy and preipheral connectors
The power supply is from Maplin and is a G7 Power extreme and I found no poor reviews about it exploding.

---

### Post by QIII on 2012-07-25
> **ahallubuntu said:**
> A new power supply could most certainly be bad.

Could.  I didn't say it couldn't.  Just unlikely.

If Haggetti is replacing a PSU because the previous one went up in smoke, it is unlikely that the problem now is his new PSU.  Much more likely that the previous PSU, in its death throes, damaged the mobo.

---

### Post by Haggetti on 2012-08-06
Thanks for all your help and advice, I had it checked professionally and they're 99% surre it's the mobo.

---

