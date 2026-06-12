---
title: "Under Ubuntu, Is it possible to use a DELL network printer?"
date: 2005-05-27
forum: Hardware &amp; Laptops
---

### Post by piggyaugu on 2005-05-27
We have a DELL 1700n network printer here. It is connected directly to the lan by the network module in the printer. it has an ip adresse. Under windows, we use a PS driver for it.

Is it possible to use it in Ubuntu 5.04???

---

### Post by piggyaugu on 2005-05-27
Yeah, i've found the answer

It is usable with the "HP Jetdirect" mode and a Dell S2500 driver.

 \\:D/

---

### Post by otherdave on 2005-05-27
[QUOTE=piggyaugu]Yeah, i've found the answer

It is usable with the "HP Jetdirect" mode and a Dell S2500 driver.

 \\:D/[/QUOTE]

I'm about to switch to Linux at home on my main desktop machine (with Ubuntu of course). I was thinking about getting the 1700n or splurging for the 3000cn and getting some color as well. Any ideas if the 3000cn would work with the same/similar driver? Where did you get your information about the 1700n?

---

### Post by shakin on 2005-05-27
[QUOTE=otherdave]I'm about to switch to Linux at home on my main desktop machine (with Ubuntu of course). I was thinking about getting the 1700n or splurging for the 3000cn and getting some color as well. Any ideas if the 3000cn would work with the same/similar driver? Where did you get your information about the 1700n?[/QUOTE]

Is the 3000cn a network printer? I believe all Dell network printers support Postscript and lpd queues. I currently print to one that *might* be the 3000cn because the name rings a bell (printer doesn't have a model name on the front). Postscript works wonderfully and the quality is high. Since I'm the only lpd user I changed my lpd queue name to my username and the LCD on the front of the printer shows my username whenever my print job is started. I've had a lot of people in the office ask me how I did it because it makes it so much easier to find my print job.

---

### Post by otherdave on 2005-05-27
Yes, it's a network printer (the 'c' means color and the 'n' means network. At least for this series of printers).

On Dell's website the 3000n lists ' PCL 6, PCL 5e' as the printer language supported. The 3100 lists ' PCL6, PCL5e, Adobe®  PostScript®  3TM' as supported so I might not have postscript if I get the 3000n.

---

### Post by piggyaugu on 2005-06-02
[QUOTE=otherdave]Yes, it's a network printer (the 'c' means color and the 'n' means network. At least for this series of printers).

On Dell's website the 3000n lists ' PCL 6, PCL 5e' as the printer language supported. The 3100 lists ' PCL6, PCL5e, Adobe®  PostScript®  3TM' as supported so I might not have postscript if I get the 3000n.[/QUOTE]

i dont know if there is a way to manage the PCL situation. Mine here is PS, it works well.

---

