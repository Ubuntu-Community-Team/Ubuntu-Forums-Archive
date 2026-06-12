---
title: "Instaling Problems"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by Absylon on 2009-02-03
Hello all;

 I bought a new graphic card (ATI Radeon HD 3870) and because of that I had a format on my HDD. Now when I tried to install the Ubuntu, after loading and when the log in sound comes up, I got no image and because of that I can't upgrade graphics or do anything.

What should I do?

Tks in advance.

---

### Post by avtolle on 2009-02-03
For my clarification: you have installed, and have the problem you posted?

---

### Post by cariboo on 2009-02-03
First of all when installing new hardware you don't have to reformat the hard drive. Remember Linux is not windows.

The black screen is caused by X being set to a resolution that your monitor can't use. I had the same problem the other day after an update. I have remote desktop enabled on that computer and logged in and reset the resolution to one that my 32" HD LCD TV could use and everything was good again.

You may be able to edit ~/.config/monitors.xml, below is a copy of mine form the computer that started wit a black screen. As you can see my resolution is set to 1360X768, I would suggest starting with 1024X 768. 

```
<monitors version="1">
  <configuration>
      <clone>no</clone>
      <output name="VGA">
          <vendor>SAM</vendor>
          <product>0x02a2</product>
          <serial>0x00000000</serial>
          <width>1360</width>
          <height>768</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
      </output>
  </configuration>
  <configuration>
      <clone>no</clone>
      <output name="VGA">
          <vendor>???</vendor>
          <product>0x0000</product>
          <serial>0x00000000</serial>
          <width>1360</width>
          <height>768</height>
          <rate>60</rate>
          <x>0</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
      </output>
  </configuration>
```

The above file is from a computer with an onboard Intel video chip set.

Jim

---

### Post by Absylon on 2009-02-03
I don't have the Linux installed now avtolle and i only formatted the HDD because of Windows really. 

Tks cariboo907 I gonna try that solution and see if I finally can have my Ubuntu back!

;)

---

