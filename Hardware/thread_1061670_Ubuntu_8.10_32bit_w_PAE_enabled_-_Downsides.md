---
title: "Ubuntu 8.10 32bit w/ PAE enabled - Downsides?"
date: 2009-02-06
forum: Hardware
---

### Post by JoelJohnson on 2009-02-06
Ok, I've searched around the forum, and I can't see anyone mention any drawbacks to enabling PAE on a desktop.

I've been messing with 64bit Ubuntu mostly because I have 4gigs of ram and I would like to have it all available. I'm getting sick of messing with guides and such to get 32apps running on my computer. (I can't even get Flex Builder to work even after following the guide on these forums :( ) It seems that a lot, if not most, apps are 32bit only, and half of those require you to follow a step-by-step procedure to get it working.

Anyway... the point - I'm thinking about starting fresh with a 32bit install. I read that if I use PAE that I'll be able to use >3G ram. My question is will I have any problems with performance in any games or anything that I might play? or anything like that.

Specs:
Lenovo Thinkpad T61p
Intel Core 2 Duo T7700 / 2.4 GHz 
NVIDIA Quadro FX 570M
4Gb RAM

Thanks.

---

### Post by jrusso2 on 2009-02-06
Its not a drawback to using PAE but not all applications will use PAE.  But the operating system should.

---

### Post by jespdj on 2009-02-06
> **JoelJohnson said:**
> ... It seems that a lot, if not most, apps are 32bit only, and half of those require you to follow a step-by-step procedure to get it working.
I don't know where you are looking for your software, but almost all open source software (including almost everything in the Ubuntu repository) is available as native 64-bit binaries. The only stuff that's 32-bit are a few proprietary programs like Skype and Google Earth, and they are not too hard to install on 64-bit Ubuntu.

There's more to 64-bit than just the ability to use more than 4 GB RAM. In 64-bit mode, the processor has more and larger internal registers available, and to get really technical, the [calling convention](http://en.wikipedia.org/wiki/Calling_convention) is different (parameters to subroutines are passed in registers instead of on the stack). These things make software run faster and more efficiently. Especially with processor-intensive applications (for example, audio and video decoding and encoding, and also games with physics computations), there can be a significant speed boost for 64-bit software. (Note that a 32-bit program running on a 64-bit OS cannot take advantage of this).

On a 32-bit system with PAE, each process still cannot allocate more than about 3 GB RAM.

---

### Post by JoelJohnson on 2009-02-06
Thanks for your replies.

I understand that a lot of opensource software has 64 bit builds. But it seems that whenever I want to try this program or that program out (Boxee, for example) I'm having to google it, go through 5-10 steps of this and that to get it working. And even then it doesn't always work, (Flex Builder, for example).  It's starting to wear on me. I just want things to work. :P

I don't know if I'm changing yet. I'm going to wait and see. But I wanted to know if PAE was really an option for desktop use with light gaming on the side. :P

Thanks again.

---

### Post by ridetheteapot on 2009-02-06
Well I'm using the 32bit server kernel with pae... I have a p. core 2, so i could have gone 64bit... if you check out 64bit vs 32bit benchmarks you'll see that really 32bit is a better choice for gaming... most advantages for x86-64 are more useful for a server then a desktop. So if you want more then 3 gigs of total memory it seems that gaming will take a hit either way you go.
I'll try benchmarking the server vs. generic kernel later, when i can reboot.

---

### Post by ridetheteapot on 2009-02-06
with phoronix-test-suite i tested the 2.6.27.11-server and generic kernels. tried the unigine (opengl), ramspeed, and openssl

short answer - of those three tests there was no preformance differences

used unigine to test game preformance (its an advanced opengl demo)
ramspeed cause i was curious if there was a direct memory speed difference
and openssl just cause x86_64 systems show a clear advantage over 32bit here, and if pae was even slower then without it, it would be like a double hit vs 64bit... but there was no difference pae or not

also tried glxgears for fun and there was no difference

guess i should note that i am using the nvidia 180.27 drivers for the gfx tests

fyi a good place to see benchmark results for different configs is here [http://global.phoronix-test-suite.com/](http://global.phoronix-test-suite.com/)
lots of user uploaded benchmarks tagged and everything

---

