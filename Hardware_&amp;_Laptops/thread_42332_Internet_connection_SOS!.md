---
title: "Internet connection SOS!"
date: 2005-06-17
forum: Hardware &amp; Laptops
---

### Post by kirandasck on 2005-06-17
Hello friends,
i just installed Ubuntu in my laptop and threw out windows.Wonderful ,fresh feeling,like a prisoner being released from jail!
   But i have a problem connecting with internet.
My laptop have an internal modem(PCI,i think)
details
  HSP56 MR(ALI+)
i tried to make a dial up connection using KPPP.
i used the port "ttsy2" for the modem as i used "COM3" in windows.
  When i tried to connect to internet some messages like " The modem is busy","The modem is not ready" etc were shown.
  Can anyone of you help me to fix this problem using the existing internal modem.
Thanks in advance,
                     Kiran.

---

### Post by intangible on 2005-06-17
[QUOTE=kirandasck]Hello friends,
i just installed Ubuntu in my laptop and threw out windows.Wonderful ,fresh feeling,like a prisoner being released from jail!
   But i have a problem connecting with internet.
My laptop have an internal modem(PCI,i think)
details
  HSP56 MR(ALI+)
i tried to make a dial up connection using KPPP.
i used the port "ttsy2" for the modem as i used "COM3" in windows.
  When i tried to connect to internet some messages like " The modem is busy","The modem is not ready" etc were shown.
  Can anyone of you help me to fix this problem using the existing internal modem.
Thanks in advance,
                     Kiran.[/QUOTE]
 Sounds like you have a winmodem, I haven't had to deal with one in a long time, so I can't specifically help, but here's a good place to start: [https://wiki.ubuntu.com//WinModemLucent](https://wiki.ubuntu.com//WinModemLucent)

Another thing to try is to install minicom and see if you can talk to the modem directly using standard AT commands.

**AT** should return "ok"
**ATD** should let you hear the dial-tone
**ATDT5555555** should dial 555-5555 (try to call a number you know and see if it rings through)

---

