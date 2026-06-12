---
title: "Has ATI open sourced their drivers yet?"
date: 2009-06-02
forum: Hardware
---

### Post by golfer91 on 2009-06-02
Hello,

I wanted to know if ATI has open sourced their drivers as of this date. I am a bit cynical because it has been such a long time and there are not any recent news on the issue, at least through a google search.

I am thinking of buying one of the new acer gemstones but the model I like comes with ATI and I want my computer to be completely functional - compiz, open arena, etc - in Ubuntu as I do not wish to return to Windows other than for gaming.

Kind regards,

---

### Post by Segraym on 2009-06-02
No, it is quite troubling getting the drivers to even work on Jaunty with an ATi card and when you do, they are extremely laggy, and can't handle full screening even music or video applications.  I'm considering switching cards just to get away from ATi.

---

### Post by cubeist on 2009-06-02
For me, ATI proprietary drivers work great, and have worked great for a couple years now.  No problems in Jaunty at all.

However, if you don't like using proprietary drivers, there is an open source project for ati video cards, and it has come a long way in the last few years as well.  Check out phoronix.com for the latest news.

If your primary purpose for moving to Ubuntu is gaming, then whether you use ATI or Nvidia, you will probably be disappointed. Yes there are some great linux games available, but the focus of the platform (linux) is generally not on gaming and there are not a lot of commercial linux games.

If you are buying a new computer, it is in your best interest to do lots of research to see if the hardware works on linux.  Linux supports a ton of hardware, but some bleeding edge hardware requires time to develop, so there may be a lag in compatibility.

---

### Post by jocko on 2009-06-03
> **fabioalma said:**
> I wanted to know if ATI has open sourced their drivers as of this date. I am a bit cynical because it has been such a long time and there are not any recent news on the issue, at least through a google search.

ATI will never open source their driver (fglrx), and they have never claimed that they will do it. The code contains parts which can never be open sourced (such as hardware acceleration of proprietary video formats and probably parts that they need to keep secret from their competitors).
However, they have released specifications for their cards together with some sample code to get the open source community something to work with instead of reverse-engineering drivers. They may even have one or a few programmers working on the open source drivers (radeon/radeonHD) to help the community.
You can read all about it on [phoronix]("http://www.phoronix.com/scan.php?page=home").

---

### Post by Fir3chi3f on 2009-06-03
> **cubeist said:**
> For me, ATI proprietary drivers work great, and have worked great for a couple years now.  No problems in Jaunty at all.

However, if you don't like using proprietary drivers, there is an open source project for ati video cards, and it has come a long way in the last few years as well.  Check out phoronix.com for the latest news.

If your primary purpose for moving to Ubuntu is gaming, then whether you use ATI or Nvidia, you will probably be disappointed. Yes there are some great linux games available, but the focus of the platform (linux) is generally not on gaming and there are not a lot of commercial linux games.

If you are buying a new computer, it is in your best interest to do lots of research to see if the hardware works on linux.  Linux supports a ton of hardware, but some bleeding edge hardware requires time to develop, so there may be a lag in compatibility.

I imagine you have a newer Ati card cubeist. The older cards have been dropped from support from the latest ati drivers and 9.04 uses the latest X-server that is incompatible with the older drivers.

---

### Post by cubeist on 2009-06-03
> **Fir3chi3f said:**
> I imagine you have a newer Ati card cubeist. The older cards have been dropped from support from the latest ati drivers and 9.04 uses the latest X-server that is incompatible with the older drivers.

most older cards work with either an older proprietary driver, or the open-source drivers.  Or if your card is that old, consider upgrading to a newer model, the 3600 series start around $30 for oem.

---

### Post by ssri on 2009-06-03
> **cubeist said:**
> most older cards work with either an older proprietary driver, or the open-source drivers.  Or if your card is that old, consider upgrading to a newer model, the 3600 series start around $30 for oem.

Try telling that to laptop users.  Mine being a HP business laptop only 1.5 years old.  Already, the chip (released Q2 2007) is deemed legacy.

---

