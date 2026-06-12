---
title: "Firefox problems"
date: 2008-07-22
forum: Hardware
---

### Post by dunbrokin on 2008-07-22
Now, why in darnation would I be getting segfaults at around 9.00 each morning?

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9) Gecko/2008062517 Firefox/3.0

Jul 19 09:32:22 PJ kernel: [69067.088509] firefox[2092]: segfault at b77de31a eip b7cc32a5 esp bff4e370 error 4
Jul 19 09:32:27 PJ kernel: [69070.701574] firefox[2125]: segfault at b77de31a eip b7cc42a5 esp bf860480 error 4
Jul 19 09:33:09 PJ kernel: [69100.049740] firefox[2188]: segfault at b78ab31a eip b7d802a5 esp bfbc5fe0 error 4
Jul 19 09:33:18 PJ kernel: [69106.271315] firefox[2194]: segfault at b77fc31a eip b7ce22a5 esp bfedab00 error 4
Jul 19 09:33:18 PJ kernel: [69106.504468] firefox[2196]: segfault at b784231a eip b7d382a5 esp bff863a0 error 4
Jul 19 09:34:18 PJ kernel: [69141.192683] firefox[2313]: segfault at b780f31a eip b7d132a5 esp bfba3f70 error 4
Jul 19 09:35:22 PJ kernel: [69182.611357] firefox[2376]: segfault at b78ab31a eip b7d972a5 esp bf81ac30 error 4
Jul 19 09:35:43 PJ kernel: [69196.020773] firefox[2389]: segfault at b784231a eip b7d4f2a5 esp bfd09920 error 4
Jul 19 09:36:07 PJ kernel: [69212.495866] firefox[2435]: segfault at b784231a eip b7d2d2a5 esp bf89fc50 error 4

Jul 21 09:05:32 PJ kernel: [54937.067570] firefox[10995]: segfault at b77de31a eip b7cb52a5 esp bfe792c0 error 4
Jul 21 09:05:54 PJ kernel: [54943.463551] firefox[11011]: segfault at b780f31a eip b7cfb2a5 esp bfd951d0 error 4
Jul 21 09:06:08 PJ kernel: [54947.656825] firefox[11022]: segfault at b77de31a eip b7cc82a5 esp bfa0ae50 error 4
Jul 21 09:06:48 PJ kernel: [54960.827239] firefox[11045]: segfault at b77ab31a eip b7cb22a5 esp bfe2ca50 error 4
Jul 21 09:30:57 PJ -- MARK --
Jul 21 09:47:38 PJkernel: [55455.908635] firefox[12471]: segfault at b789831a eip b7d7e2a5 esp bff13330 error 4
Jul 21 10:10:57 PJ -- MARK --
Jul 21 10:20:49 PJ kernel: [55845.202072] firefox[13689]: segfault at b780f31a eip b7cf02a5 esp bfef0330 error 4

Jul 22 09:03:29 PJ kernel: [72040.388764] firefox[2467]: segfault at b784231a eip b7d1a2a5 esp bfec8300 error 4
Jul 22 09:04:22 PJ kernel: [72055.471951] firefox[2500]: segfault at b789831a eip b7d702a5 esp bfa826a0 error 4
Jul 22 09:17:29 PJ kernel: [72232.305157] firefox[2959]: segfault at b77de31a eip b7cc32a5 esp bff74390 error 4
Jul 22 09:17:34 PJ kernel: [72234.588301] firefox[2965]: segfault at b780f31a eip b7cf12a5 esp bfeda300 error 4
Jul 22 09:17:43 PJ kernel: [72239.580539] firefox[2973]: segfault at b77fc31a eip b7ce12a5 esp bfa7e6a0 error 4
Jul 22 09:17:54 PJ kernel: [72245.009708] firefox[2978]: segfault at b77fc31a eip b7cdb2a5 esp bfec92f0 error 4

Jul 23 09:06:30 PJ kernel: [87974.063622] firefox[21221]: segfault at b78ab31a eip b7d8c2a5 esp bffa53c0 error 4
Jul 23 09:07:54 PJ kernel: [87996.370541] firefox[21269]: segfault at b78ab31a eip b7d992a5 esp bff6ebb0 error 4
Jul 23 09:08:24 PJ kernel: [88003.286130] firefox[21292]: segfault at b780f31a eip b7ceb2a5 esp bfa3a680 error 4
Jul 23 09:08:30 PJ kernel: [88005.812194] firefox[21297]: segfault at b78ab31a eip b7d982a5 esp bf9945d0 error 4
Jul 23 09:08:53 PJ kernel: [88011.521658] firefox[21311]: segfault at b77fc31a eip b7cd82a5 esp bf9a6de0 error 4
Jul 23 09:08:59 PJ kernel: [88014.237486] firefox[21316]: segfault at b78ab31a eip b7d922a5 esp bff23b60 error 4
Jul 23 09:30:58 PJ -- MARK --
Jul 23 09:50:58 PJ -- MARK --
Jul 23 10:10:58 PJ -- MARK --
Jul 23 10:25:24 PJ kernel: [177556.636962] ipw2200: Firmware error detected.  Restarting.

---

### Post by ProbablyX on 2008-07-22
Might be some hardware thats faulty, and is being accessed everymorning at that time via a cron job or other schedual program.

Do you have any such jobs going, programs that run at a certain time everyday that is? I had a problem involving a faulty RAM chip, causing me to get sig errors everytime I used over 1GB of RAM (as I had 2x1GB RAM, and I'd segfault everytime the second was being used)

---

### Post by dunbrokin on 2008-07-22
> **ProbablyX said:**
> Might be some hardware thats faulty, and is being accessed everymorning at that time via a cron job or other schedual program.

Do you have any such jobs going, programs that run at a certain time everyday that is? I had a problem involving a faulty RAM chip, causing me to get sig errors everytime I used over 1GB of RAM (as I had 2x1GB RAM, and I'd segfault everytime the second was being used)

I have a similar set up to you i.e 2X1GB...I have run Memtest with no adverse results. Does it really matter that I am getting segfaults...what does it do...I cannot detect anything apart from what appears on the log!

---

### Post by steveneddy on 2008-07-22
Whoh! That's weird!

---

### Post by dunbrokin on 2008-07-22
> **ProbablyX said:**
> Might be some hardware thats faulty, and is being accessed everymorning at that time via a cron job or other schedual program.

Do you have any such jobs going, programs that run at a certain time everyday that is? I had a problem involving a faulty RAM chip, causing me to get sig errors everytime I used over 1GB of RAM (as I had 2x1GB RAM, and I'd segfault everytime the second was being used)

Only cron job happens every 4 hours on the hour i.e 0,4,8,12 and checks for Ubuntu update and Thunderbird update.

---

### Post by dunbrokin on 2008-07-23
> **steveneddy said:**
> Whoh! That's weird!

I have got a handle on this now...My email program is Thunderbird...when I get an email from FT.com and click on the link to go to the website in FF I get a segfault.....

---

