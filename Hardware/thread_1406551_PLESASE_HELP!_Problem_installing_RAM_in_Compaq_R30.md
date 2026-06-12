---
title: "PLESASE HELP! Problem installing RAM in Compaq R3000"
date: 2010-02-14
forum: Hardware
---

### Post by buddhaflow on 2010-02-14
Hey, I've got a problem that is driving me crazy.

I'm trying to install a 1GB RAM stick into my laptop.

The laptop comes with a 2x256MB setup. Only one of the sticks is physically accessible. So the maximum memory in the specs is 1.25GB.

The stick is PC2700, same as the old stick. I am sure it is installed correctly. I took all static precautions.

The BIOS recognizes the RAM - 1.25GB total.

But Ubuntu just won't. I've got both 9.10 x64 and 9.04 x32 installed. Neither will boot. Memtest only shows the 768k of base RAM, and NONE of the extended RAM shows up - not even the initial 256MB.

I tried turning on boot logging, but the /var/logs/boot was still empty. When I turn off the splash screen, I see a whole mess of errors, which basically stem from the fact that there is no extended memory.

What the hell is happening? This is the second RAM stick I've tried, so I'm pretty sure that's not the problem. I only have two days to decide whether to return it! Please help, do you have any advice?

---

### Post by mandyb on 2010-03-23
I only had luck using a matched pair on this machine even though specs say you don't need pairs.  *BUT* he's 5 years old now and it could be he needs the older lower density modules.  If you get a PC2700 module specced for an Apple powerbook it will work for sure.  The under the keyboard module is not too tough to get at either.
Mandy B

---

