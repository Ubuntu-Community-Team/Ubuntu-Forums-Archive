---
title: "Raw data to sound card interface software"
date: 2008-08-17
forum: General Help
---

### Post by Vaedrah on 2008-08-17
Hi all

I am new to Linux/Ubuntu but also use XP and Vista on other machines. However I'd like to know if anyone can suggest software (s/w) that can interface a (notebook) sound-card (in either Ubuntu or XP or Vista) to raw (text array) data.

I'd like to use this combination as a general purpose dual channel source for arbitrary signal synthesis (left speaker channel, right speaker channel) and as a single channel signal acquisition input (microphone). 

Although I have seen some oscilloscope s/w etc these applications are of little use as I intend to process the raw data on MathCad, MATLAB or Octave.

Also high level programs such as LabView or HpVee are well beyond my budget and I prefer to find an application that is either "freeware" or has a demo version (with appropriate drivers)

In addition I need a text format corresponding to ADC or DAC bit codes as this will directly interface with my maths s/w, however 2's compliment is probably OK.

This "off machine" processing does not need to be real time and don't mind using a number of conversion programs if need be.

Anyway I look forward to any suggestions :)

---

### Post by kaspar_silas on 2008-09-10
I really like the idea of using the mic channel and sound card as a signal channel DAQ system. However I guess it's AC coupled which is a bit of a pain.

I previously myself done this in labview but it would be great to be able to do it on any system. Did you work out how to do it?

---

### Post by TestGuru on 2009-05-22
I would suggest Multi-Instrument (fully functional free trial downloadable at: [www.multi-instrument.com/MIsetup.exe]("http://www.multi-instrument.com/MIsetup.exe").). It supports text output via either copy & paste or export,  and can read the values of every single data pint in the graph via its cursor reader.

---

