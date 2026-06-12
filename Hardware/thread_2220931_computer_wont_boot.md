---
title: "computer wont boot"
date: 2014-04-30
forum: Hardware
---

### Post by pdlethbridge on 2014-04-30
I'm doing a new build with all new part but All I get is a fan turning brifly in the case and on the mother board Do I have a doa power supply or what other posibilitys?  THANKS IN ADVANCE:confused:[http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)

---

### Post by carl4926 on 2014-04-30
Some MB have a capacitor that needs to charge, leave it all connected 10 mins and try again

Double check all connections

Can you try another PSU?

---

### Post by grahammechanical on 2014-04-30
You might want to check that the RAM chips are properly seated. Re-check all the wiring. Is the CPU properly connected? Is the RAM and CPU compatible with the motherboard?

There are two essential components without which a computer motherboard will not work and they are RAM and CPU. If they are compatible and fixed correctly and not damaged the motherboard will first access an integrated circuit that contains a program called BIOS/UEFI that tells the motherboard what kind of machine it is and from the information in that integrated circuit the motherboard will run its Power On Startup Tests (POST). All this can take place without an operating system being installed. But it needs RAM and CPU to get that far. And we need a graphic adapter and monitor to see the output from those tests.

Regards.

---

### Post by LastDino on 2014-04-30
I suspect power-supply issue. Just in case check all the connections and RAM, but best thing would be to get some other PSU and check it.

---

### Post by oldfred on 2014-04-30
With my old motherboard if video card did not work it behaved like a totally dead system. 

If you have voltmeter, you can carefully jumper two pins and then check voltage. I found instructions on Internet somewhere and was able to check every pin for correct voltage.

But I would double check all connections and if everything is seated securely.

---

### Post by carl4926 on 2014-04-30
I had a machine in a week or so ago and it seemed dead. So I pulled the PSU and replaced it. All system were go.
Tested the dead one again. It was dead. (But under warranty)
Sent it back to manufacturer. They said it was OK and sent it back. Didn't get round to testing it yet. But the original machine is back with the customer....

:P

---

### Post by pdlethbridge on 2014-04-30
I took oldfreds advice andcheck all the conections and 















i founhd a pin mising on the large mobo connecter When I flipped the cable over and looked at the pins  the one to the lef5t of the hook that holds it to the mobo was missing I would asume it was designed with that pin

---

### Post by oldfred on 2014-04-30
Some connectors do have blank pins for some reason.
So do not know for sure.

---

### Post by LastDino on 2014-05-01
If you're talking about one of the top  pins on PSU main connector to mobo, those are suppose to be your ground and if you've small connector to mobo from PSU 4-pin available, it really matters not whether it is there or not. My PSU doesn't even have those top4 pins. It only has 20 on main and that other small 4-pin connector to do the job of those missing.

---

