---
title: "Application to control fan speed"
date: 2014-02-26
forum: Hardware
---

### Post by maazmahmood on 2014-02-26
My fan on the CPU is WAY too loud, is there a way to control fan speed? And please no apps that just show fan speed, but some that control it as well

---

### Post by QIII on 2014-02-26
Hello!

Have you determined WHY your fan is running so fast?  Best to look into that before trying to slow it down.

Cheers!

---

### Post by Mark Phelps on 2014-02-26
> My fan on the CPU is WAY too loud,

Most likely, it's loud because your CPU is running hot, and the fan has to run FAST in order to cool it down.  

IF you artificially slow down the fan, you will burn up the CPU and/or crash the PC.

---

### Post by maazmahmood on 2014-02-26
I've looked at the temperature of the CPU it's like stable 24-30 degrees

---

### Post by QIII on 2014-02-26
Does your motherboard support Cool 'n Quiet (AMD) or SpeedStep (Intel) control of the CPU fan speed and is it enabled?

---

### Post by tgalati4 on 2014-02-27
Sometimes fans go to full speed when the motherboard's pulse width modulation (PWM) circuitry fails.  Boot into BIOS and see if you can monitor fan speeds and perhaps control the trip points.

---

### Post by maazmahmood on 2014-02-27
This is an old motherboard 

Full specs can be found here:
[https://drive.google.com/file/d/0B401Ci0KQvVranRkMFkzLXFVTHM/edit?usp=sharing](https://drive.google.com/file/d/0B401Ci0KQvVranRkMFkzLXFVTHM/edit?usp=sharing)

---

### Post by QIII on 2014-02-27
That board should support PWM control of the HSF.  Is this something that is happening only under Linux, or Windows, too?  Has it only recently started?

---

### Post by maazmahmood on 2014-03-01
No pretty much, when I used my old desktop to boot install Ubuntu it started. I ignored because I had to get the OS up and running, but now it's kind of annoying and has gotta go

---

### Post by tgalati4 on 2014-03-01
Some people take a 12VDC fan and convert it to a 7VDC fan.  You take the leads from the 12VDC and 5VDC and you get a 7VDC differential.  This makes the fan run slower and thus quieter.  Some 12VDC fans will run at 5VDC so you can try that as well.  A slower fan will mean that your CPU will get hotter.

Otherwise, get a new CPU heatsink with a large, slow rotation fan.  They are nearly silent.  But you have to get something that will attached to your motherboard and have enough room so it fits.  The other option is just to get a larger, quieter fan and attached it somehow to your existing heat sink.  Hot glue works well.  

Otherwise, disconnect the fan and run your machine for a few minutes and see how hot it gets.  If it stays below 50C, then you should be OK.

If you want loud, get a Dell PowerEdge 1750 server with 7 fans that run at 6700 RPM and go up to 15,000 RPM during an alarm condition.  It sounds like an airplane.

---

### Post by Olav on 2014-03-01
Install the lm-sensors and fancontrol packages. Lm-sensors is a hardware monitoring programme. Fancontrol is a daemon to control your fan speeds and it comes with the pwmconfig programme to configure it. These can be tricky to set up and it requires a bit of knowledge about your system but there are howtos and tutorials to be found on the web.

Unfortunately as far as I know there are no GUI programmes (at all) that allow you to control your fans in Linux/Ubuntu, like they exist for Windows. But if you can get fancontrol running it is a superior solution.

Also remember that the standard CPU coolers provided by Intel and AMD are often of inferior quality. The heatsinks are mostly just big enough for very modest use and the fans are also too small and then spinning much too fast to compensate. Which of course wears out the bearings so they become even louder over time. And when you want to replace just the fan it often turns out they are of non-standard dimensions.

So, in addition to using fancontrol you may want to invest a bit in a better & quieter cooling solution for your CPU. It doesn't have to be terribly expensive; an example of a reasonably nice and affordable cooler is CoolerMaster Hyper TX3 EVO, but there are many others. If you go shopping you have to watch for a cooler that fits on your CPU socket and in your computer case. The attached fan will need to have the 4-pin PWM connector that allows for speed control.

---

### Post by maazmahmood on 2014-03-04
could you please provide the commands for each of those please

---

### Post by Yellow Pasque on 2014-03-05
> **tgalati4 said:**
> Some people take a 12VDC fan and convert it to a 7VDC fan.  You take the leads from the 12VDC and 5VDC and you get a 7VDC differential.  This makes the fan run slower and thus quieter.
Caution has to be taken with the 7V trick: [http://www.silentpcreview.com/article6-page1.html](http://www.silentpcreview.com/article6-page1.html)

> Otherwise, disconnect the fan and run your machine for a few minutes and see how hot it gets.  If it stays below 50C, then you should be OK.
Bad advice. You would have to test it under extended load and that would probably cause the CPU to overheat quickly. Unless you have a very large heatsink and/or a low power CPU, then passive cooling won't work.

---

### Post by maazmahmood on 2014-03-09
Could I get the commands then please?

---

### Post by Yellow Pasque on 2014-03-09
```
sudo apt-get install lm-sensors fancontrol
pwmconfig #I can't remember if it needs sudo/root permissions
```

---

