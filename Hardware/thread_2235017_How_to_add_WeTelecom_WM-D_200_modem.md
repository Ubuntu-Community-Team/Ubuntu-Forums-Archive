---
title: "How to add WeTelecom WM-D 200 modem"
date: 2014-07-18
forum: Hardware
---

### Post by mhmdsmn on 2014-07-18
Hi ...My operating system is xubuntu 14.04
and it doesn't seem to recognize the WeTelecom WM-D200 modem..I am a linux newbie with no experience whatsoever in programming
please I need a step by step tutorial on how to make this modem work

---

### Post by Vladlenin5000 on 2014-07-18
Have you checked the network manager already?
Most modems nowadays are recognized after a few seconds (<30s) and you just have to do the initial setup by choosing country, carrier and specific data plan, if applicable.

---

### Post by Vladlenin5000 on 2014-07-18
[https://www.youtube.com/watch?v=yAqEFhqRr_I&html5=1](https://www.youtube.com/watch?v=yAqEFhqRr_I&html5=1)

---

### Post by mhmdsmn on 2014-07-18
Still no go...please help...I tried what was described in the video description (though it was in russian) but still no go

---

### Post by mhmdsmn on 2014-07-27
I know that I have to make my system recognize the modem by adding the following
/* WeTelecom products */
#define WETELECOM_VENDOR_ID                     0x22de
#define WETELECOM_PRODUCT_WM_D200               0x6801
to a file in my system....Problem is I don't where this file is....my operating system is xubuntu 14.04 xfce and it differs ,slightly, from the full ubuntu distro

---

