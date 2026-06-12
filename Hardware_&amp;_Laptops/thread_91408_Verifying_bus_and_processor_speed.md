---
title: "Verifying bus and processor speed"
date: 2005-11-17
forum: Hardware &amp; Laptops
---

### Post by HackSawtooth on 2005-11-17
Hi.  Im just wondering if theres a way to verify my system bus speed and processor speed.  I am aware of the devices list under the admin menu.  That did not show me bus speed.  Is there a way using the terminal?

Thanks

Chris P

---

### Post by Teroedni on 2005-11-17
sudo lshw

---

### Post by HackSawtooth on 2005-11-20
OK that is the command I was looking for.  However, surprisingly, does not report that actual bus or processor speed of my system.  Im sure this problem is somewhat unique to my system board.  I think I am the only person on the planet running a Sawtooth G4 motherboard with an overclocked bus.  My bus is actually 120MHz, but both Mac OS X and Ubuntu see it as 100MHz.  My system realizes the proper multiplier, and reports a 500MHz processor speed when it should be 600MHz.  Not sure why exactly this happens, its not incredibly important, but I would like to find out.

---

### Post by HackSawtooth on 2005-11-27
Turns out firmware has to be modified to report the proper speed of my modified board.  Kind of annoying but it works.

---

### Post by Teroedni on 2005-11-28
Great to hear:)
Could you add a [Solved] to the thread name please:)

Thanks in advance:KS

---

### Post by HackSawtooth on 2005-11-28
Like that?

---

