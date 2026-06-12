---
title: "What kernel to use with Athlon XP 2100+"
date: 2005-04-25
forum: Hardware &amp; Laptops
---

### Post by codejunkie on 2005-04-25
I have an AMD Athlon XP 2100+ Processor and ubuntu works fine but it installs with 
the linux-image-2.6.10-5-386  i tried k7 kernel and xorg broke i reinstalled and tried the k7 kernel again and added the linux-restricted-modules-2.6.10-5-k7 and it worked
but what is difference between kernels and what are the gains because i've noticed no better speeds. also can it damage my hardware buy using the k7 kernel because it shows up as an i686 machine and ubuntu automaticly set's it up using the i386 kernel and im a ex suse user that's has never had to deal with this choice before. :-k  
any help would be appreicated.

---

### Post by heimo on 2005-04-25
I think this is in FAQs or Howtos, but I'm too lazy to search second time.
 
I'm using Athlon 2600+ and when I was selecting pre-packaged kernel, I searched which one is best for me and the suggestion was to use -686. I don't know if it's at all faster than the -386. If I recall correctly, -K7 is for older AMDs, but should work for newer ones too.
 
:)

---

### Post by bailout on 2005-04-25
Unfortunately there seems to be no definitive answer to this question. Some people use k7 others 686. It is annoying that such a basic question that affects so many users hasn't had a clear answer from the developers. See these threads.

[http://www.ubuntuforums.org/showthread.php?t=22218&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=22218&page=1&pp=10)

[http://www.ubuntuforums.org/showthread.php?p=147090](http://www.ubuntuforums.org/showthread.php?p=147090)

---

### Post by codejunkie on 2005-04-25
[QUOTE=bailout]Unfortunately there seems to be no definitive answer to this question. Some people use k7 others 686. It is annoying that such a basic question that affects so many users hasn't had a clear answer from the developers. See these threads.

[http://www.ubuntuforums.org/showthread.php?t=22218&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=22218&page=1&pp=10)

[http://www.ubuntuforums.org/showthread.php?p=147090](http://www.ubuntuforums.org/showthread.php?p=147090)[/QUOTE]

This is the reason i asked i searched the forums and could'nt find any specific answer either it seems like **Burger King** :) *have it your way*;). almost every one that has a athlon chip uses a diffrent kernel. this choice kinda confuses suse refugees 
like me i've never had to choose between 386, 686, or k7. yast set's up the default  kernel and you updates it that's the only time i remember seeing a kernel package.

---

### Post by heimo on 2005-04-25
I am not a developer. (IANAD) But I can guess that these -686 -k7 refer to gcc flags. Probably -march, but some other optimizations may be different too (-mtune).

How much these optimizations make difference is one question, but what we're after here is probably the question, which one is the correct one. It's a valid question. (Is my processor using all its extensions? For example 3DNow!, SSE, SSE2)

Here are some flags for gcc 3.4:
[http://gcc.gnu.org/onlinedocs/gcc-3.4.2/gcc/i386-and-x86_002d64-Options.html#i386-and-x86_002d64-Options]("http://gcc.gnu.org/onlinedocs/gcc-3.4.2/gcc/i386-and-x86_002d64-Options.html#i386-and-x86_002d64-Options")

Hmm.. And let's not make this thread a flame war about if this is important or not. Question is simple. Which kernel for my CPU (in this case Athlon XP). My new guess is that the K7 one is correct. Probably choosing 386, 686 or K7 doesn't make much difference performance wise.

And of course, everyone is free to compile their own kernels, with über maximized optimizations. :) It also makes you to know more about the hardware you're using. Try to compile only the stuff you need. It was my hobby several years ago - can I still get something out? (without losing functionality)

:) Let's keep it fun. Let's try to find those answers to our geeky questions.

Thank you!

---

### Post by bailout on 2005-04-25
heimo, this is why I still have doubts about whether the k7 is the best one for the latest amd chips. K7 was the pre-release code name for the original Athlon which only had AMD extensions IIRC. The latest Athlon family have incorporated many of the Intel extensions such as sse. Therefore the 686 might be the better choice. Unfortunately the descriptions with the files are not clear and there has been no clarification from the developers. Hence we have the current confusion with people using different kernels. It seems a bit pointless to make optimised kernels available if it isn't clear which one to use.

codejunkie, I did exactly the same thing, searched and found conflicting advice, then posted and got conflicting advice ](*,)  Maybe one day we will have a clear answer.

---

### Post by codejunkie on 2005-04-26
i don't know either but suse, slack, and fedora used an i686 kernel so i guess im going to stick with that because the k7 kernel seemed to give me a little trouble don't really know if this the right one but it works :) no worries though this is what makes linux so great i get try everything and keep what i like. ;-)

---

