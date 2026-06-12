---
title: "Frequent dead freeze with AMD ryzen 2500u laptop."
date: 2018-06-16
forum: Hardware
---

### Post by Saisankar_Gochhaya on 2018-06-16
I recently got an Acer Swift 3 powered by AMD ryzen 2500u and currently setup with Ubuntu 18.04 LTS. I get frequent dead freeze on the laptop, at least 2-3 times a day, where even ALT + PrntScn + REISUB also doesn't work. I tried upgrading my kernel to 4.17.2-041702-generic also, still no avail. Please help with this. I did a ```
journalctl --since "1 hour ago"
``` but the error seems to change from crash to another. Here is the log - [https://pastebin.com/wJWY7RNg](https://pastebin.com/wJWY7RNg) (crashed around 17:06). Thank you for all the help.
Has been months since I have posted this, still, haven't found a solution to this.

---

### Post by proton-byte on 2018-07-18
I also got freezes on my Thinkpad E485 with the Ryzen 2500u. Furthermore I've all updates installed (Ubuntu 18.04) with the newest stable kernel v4.17.8.
In the kernel options, at the grub start options, I added "noapic" and "idle=nowait" but no improvements (but I had to add "noapic" to get Linux even to boot with the 2500u).

---

### Post by kuraiskrap on 2018-09-16
Yeah, mine crashes booting up, like half the time, i posted thread, but didnt get a reply
wonder if mobile ryzen has issues?

haven't had it crash once it was up and running.
but i haven't used it much. im mostly trying to get used to the new OS
built a hackintosh for OSX. and figured id try n dual boot my laptop for school since theres a linux course next term

---

### Post by wildmanne39 on 2018-09-16
Hello kuraiskrap please do not post about your issue or a link to your thread in someone else's thread, if you do not get a reply in your thread you can bump it back into view once every twelve hours.

Thanks

---

### Post by mathes-klepper on 2018-12-07
I hope this will help for others. I have a thinkpad e485 with a ryzen 2500u. After trying lot of solutions I finally found the problem. Just disable CPU Power Management in BIOS did the trick for me. My Thinkpad runs now for 3 days without reboot. Before that I had freezes like 4 times a day.

---

