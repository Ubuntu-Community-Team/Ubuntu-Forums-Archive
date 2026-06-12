---
title: "Help me determine if I can install an extra fan"
date: 2023-05-05
forum: Hardware
---

### Post by jonfisher on 2023-05-05
Ubuntu 22.x lts

My computer is the HP EliteDesk G1 SFF 

Help me to determine if I can install an extra fan - even if I have to buy a mini fan & duck tape it in there.  I'm most interested in if there is an extra plug in for a fan in there (that would allow the computer to control when the fan turns on/speeds up/etc...)

This is the inside of my computer:

[https://www.pchouse.ro/media/catalog...or_4_2_1_1.jpg]("https://www.pchouse.ro/media/catalog/product/cache/1/image/9df78eab33525d08d6e5fb8d27136e95/h/p/hp-elitedesk-800-g1-sff-interior_4_2_1_1.jpg")

---

### Post by Dennis N on 2023-05-05
Do you have the user manual? usually it has a diagram showing where the fan connectors are. The fan connectors are usually labeled 'Fan 1' 'Fan 2' ... on the board itself, so you can visually look for them. They have 4 prongs in a line. Also, fans are managed in the BIOS, so it should show the possible fan connections and their settings.

---

### Post by jonfisher on 2023-05-05
Also, if anyone could recommend a fan/mini fan on Amazon I would much appreciate it!

---

### Post by jonfisher on 2023-05-05
> **Dennis N said:**
> Do you have the user manual? usually it has a diagram showing where the fan connectors are. The fan connectors are usually labeled 'Fan 1' 'Fan 2' ... on the board itself, so you can visually look for them. They have 4 prongs in a line. Also, fans are managed in the BIOS, so it should show the possible fan connections and their settings.

Yes, I'm looking for the users manual now, I have several pdf files.

Ok, this is what I found.

---

### Post by Dennis N on 2023-05-05
All I can see on their illustration is the CPU Fan connector (CPUFAN). There is an adapter cable called a fan splitter that allows you to run two fans from one connector. That might be posslble.

[https://www.newegg.com/p/pl?d=fan+splitter](https://www.newegg.com/p/pl?d=fan+splitter)

---

### Post by jonfisher on 2023-05-05
> **Dennis N said:**
> All I can see on their illustration is the CPU Fan connector (CPUFAN). There is an adapter cable called a fan splitter that allows you to run two fans from one connector. That might be posslble.

[https://www.newegg.com/p/pl?d=fan+splitter](https://www.newegg.com/p/pl?d=fan+splitter)

Do you think this box could take a regular size fan, even if I ducktape it in.  Or would you recommend a mini fan.

Attached is a different view - please tell me if you see a fan connector.

---

### Post by jonfisher on 2023-05-05
Also, would a different fan, maybe with coolant, be suggested and is cost minded.

Also, this attachment

---

### Post by aljames2 on 2023-05-05
Fans run within enclosures.  Perhaps a smaller extra fan would work on a shared power connection and if there is a mount point existing for the extra fan.  I wouldn’t go nascar on it with the duct tape lol.  Is the stock cooling not enough in that case?

---

### Post by Dennis N on 2023-05-05
In your post #6, they didn't identify the CPU fan connector. I suggest you be cautious before investing and google "share CPU fan connector" and do some reading to see if sharing can work with that. I know you can share the case fan connectors but you don't have any case fans or case fan connectors.

---

### Post by jonfisher on 2023-05-05
Can anyone think of any reason this fan wouldn't work?  I will also buy an extra wire that extends my current fan being able to be hooked up too.


Before I order the expansion wire, how many pins does the wire need to hook into?


[https://www.amazon.com/Kingwin-CF-08LB-Efficient-Excellent-Ventilation/dp/B002YFSHPY/ref=sr_1_19?crid=72R9AVD3KVGM&keywords=pccooler%2Bmini%2Bfan&qid=1683308228&sprefix=pccooler%2Bmini%2Bfan%2Caps%2C107&sr=8-19&th=1](https://www.amazon.com/Kingwin-CF-08LB-Efficient-Excellent-Ventilation/dp/B002YFSHPY/ref=sr_1_19?crid=72R9AVD3KVGM&keywords=pccooler%2Bmini%2Bfan&qid=1683308228&sprefix=pccooler%2Bmini%2Bfan%2Caps%2C107&sr=8-19&th=1)

---

### Post by jonfisher on 2023-05-05
I settled on this fan with a 4 pin extender wire

[https://www.amazon.com/gp/product/B071W93333/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1](https://www.amazon.com/gp/product/B071W93333/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1)

---

### Post by Dennis N on 2023-05-05
Looking at post #10, it has 3 wires. It can plug onto either 3 or 4 pin connector (header) on the board (3 wires means it is controlled by the voltage supplied - lower the voltage and it slows down). The 4th pin is for PWM controlled fans. The connector has guides to be sure it connects to the 3 correct pins if there are 4 on the header. You plan to share the CPU fan header?

In general, small 80mm fans are noisier and inexpensive fans in general can be noisier.

---

### Post by Dennis N on 2023-05-05
In post #11, that's better quality. Its PWM so needs a 4 pin header for PWM to function, but it will work with 3 pin header as well. PWM = Pulse Width Modulation. You can look that up.

---

### Post by Yellow Pasque on 2023-05-07
You have no extra fan headers and no (Molex) connecters on the PSU (that would have been too easy). If you don't want to mess with splitting the CPU header, an adapter like this may work if you have an extra SATA power cable available. [https://www.newegg.com/p/1W7-00RP-000P1](https://www.newegg.com/p/1W7-00RP-000P1)
I'm not sure if you'll have an extra SATA power connector, since your system doesn't have the SATA power connections coming from the PSU as normal, but rather from a connector on the motherboard itself.

---

### Post by Yellow Pasque on 2023-05-07
If you can't get the fan you bought working, a USB fan could be an option if you have a free USB connection on the back of the computer (punch out a PCI slot cover and run the wire through there): [https://www.newegg.com/p/1YF-00DS-00120?Item=9SIAEF87K20914&Description=usb%20fan&cm_re=usb_fan-_-9SIAEF87K20914-_-Product](https://www.newegg.com/p/1YF-00DS-00120?Item=9SIAEF87K20914&Description=usb%20fan&cm_re=usb_fan-_-9SIAEF87K20914-_-Product)

---

### Post by jonfisher on 2023-05-11
I sent the fan back, as it did nothing for the high temps during PS2 emulation

I got this ordered as someone suggested it, if anyone here thinks this won't keep the desktop cool, please tell me now as I STILL have time to cancel the order:

[https://www.amazon.com/gp/product/B0B8CVSFVY/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1](https://www.amazon.com/gp/product/B0B8CVSFVY/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1)

---

### Post by aljames2 on 2023-05-11
Not sure from your OP what your current video source is (card, onboard, etc).  I do not see a gpu card so perhaps onboard/cpu video?  It may be possible to use that new card.  If your goal is to reduce temps, adding a GPU card may not accomplish that goal.  PS2 emulation sounds like a system intensive purpose.  Your issue may be more related to the volume of air within your enclosure vs the circulation of that air.  I don’t see very many outlets from which intake and exhaust can occur.  Have you considered a slightly larger case?  Perhaps a mini tower.

---

### Post by Autodave on 2023-05-11
Or just try leaving the side panel off altogether.  Even more, a USB fan blowing inside the case through the removed side panel may help.

---

