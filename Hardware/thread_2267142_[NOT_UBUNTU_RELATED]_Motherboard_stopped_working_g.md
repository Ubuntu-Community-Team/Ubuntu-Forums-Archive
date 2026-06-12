---
title: "[NOT UBUNTU RELATED] Motherboard stopped working gtx 970(rant included)"
date: 2015-02-27
forum: Hardware
---

### Post by barkerson on 2015-02-27
Note before reading this that I'm writing this from my school laptop which have problems even running minecraft:(.(possible thread moving might be needed if I'm posting this in the wrong place)

So at christmas I got myself(my parents got) an Asus GTX 970 SC, and it stopped working. Or at least the motherboard did after two weeks(not compleately).
I have an asus p8z68 -pro motherboard in the centre of my build(it's ~4 years old at the time) running linux(+ windows after christmas) and for some reason it randomly stopped working, you might ask "but why didn't you look for help earlier?", I did. The RMA time in total with shipping took about 1 month more or less + me being forced to pay shipping and work to get it returned. Me hoping the issue got resolved took and slapped the card back in my pc (it works with a GTX 560 at the moment, and before the whole ordeal). No bios, just a blank screen with the text "PRESS DEL TO ENTER BIOS", much like the time before when I initially thought the card was bricked.
Then today, the day I got it back, I looked through the house like a savage assemblying a pc with some parts from as early as about 2004(ddr2 and lga755). I then proceeded to test the machine with the GTX 560 and 970, both worked... wait, WHAT?!
For some unknown reason the old motherboard, with no screws, slightly bent from when I forced the cpu fan on there, worked flawlessly passing bios with no messages other than there being no keyboard attatched and there being no drives attatched. This, while the newer motherboard can't even get past the bios screen and just sits there taunting me, making a clicking sound everytime I press a key:mad:. The strange thing was that this happened right after I changed the boot order in bios to go back to linux after playing some games.(grub didn't seem to find my win 7 install). Could this be related in any way?

Is there any possible way to fix my mobo/bios to let me use my gpu  again? I don't have the money to go out and get a new basic one +  processor just to get this working. If anyone has any tips or tricks,  specific guidelines to help me or just know something, please help, I'm  in need of it right now.

TLDR;
I have been running linux for these ~4 years with no issue AND the mobo decided to stop working right after using windows once with my new 2 weeks old graphics card(old still works though). To broke to get new mobo, help much appreciated.

---

### Post by Yellow Pasque on 2015-02-27
The first thing I would try is resetting the CMOS.

My theory is that the problem has something to do with the "Lucid Virtu" feature of the mobo, which is why it didn't manifest itself until you booted into Windows, which supports that feature (and I don't think Linux does). I would try disabling that feature in the BIOS (it's in the Advanced section as is my understanding) and then attempt to install and boot with the 970.

Another possibility is that your board is one of the P8Z68 boards that officially advertised PCI-e 3.0 speeds, but for some reason, doesn't actually work with PCI-e 3.0 GPU's (I think the 970 is 3.0 while the 560 is 2.0). I really doubt that or it wouldn't have worked for two weeks before refusing to boot. Nevertheless, if you want to rule that out, you can force PCI-e 2.0 speeds in the BIOS if your BIOS allows it.

---

### Post by barkerson on 2015-02-27
Oh my god... I looked up what the software is and it's basically: "igpu gives assistance to main gpu!", or as more people use it: "get yo' screen output from anotha' port on yo' pc!" which doesn't really work on a processor without a igpu(i7 3770k)...
I'm too tired and pissed of right now to try and fix, but I'll be back tomorrow and report if I was able to fix it. Thanks for your help, I'm still a bit pissed though that RMA + shipping costs ~$65 and took a month.

---

### Post by Yellow Pasque on 2015-02-27
Yeah, it's rarely a good idea to deal with mobo companies' tech support. Either the mobo works when you get it and you keep it, or it's DOA/incompatible and you send it back to the vendor within 30 days for a small shipping/restocking fee. If it dies or has problems outside of the initial vendor warranty period, you're usually better off getting a brand new mobo than to try and deal with the likes of Asus or other mobo companies.

If it turns out to be the Lucid Virtu "feature" that caused the problem, then you should demand refund of your $65 because the tech support rep should have been able to diagnose that. Usually, I subscribe to the theory that one catches more flies with honey than vinegar, but when it comes to dealing with low-level mobo tech support, it may be necessary to be get aggressive. Demand to speak to a supervisor or threaten legal action if you have to. Good luck.

---

### Post by barkerson on 2015-02-27
I initially thought it was an error with the graphics card(since it worked with the 560), so I only went to the store my parents bought it and they sent the gpu to get error checked, can't get refund on a service which doesn't show an error unfortunetly... now I seriously gotta sleep.

---

### Post by barkerson on 2015-02-28
I think I'll discuss it with eitherr asus because their mobo feature shouldn't disable a gpu, or I'll contact EVGA(I wrote the wrong name in the first post) because their card should be compatible(not care) with a feature that shouldn't even matter.

[edit] Contacting asus now. wait like a day or two until I get an answer.

---

### Post by barkerson on 2015-02-28
Ok, I found the source of the problem from another random forum someware, it was the "Intel Speedstep Technology" that brought havoc upon my system. Disabled it, IT WORKS!

But seriously, they need to make a patch for this ASAP. I'll be happy when they find that this is the source of all evil jan/2015... Thanks for all the help, I appreciate it. Now I just have to make the Nvidia drivers work again :P

---

