---
title: "Trying to install 8.10 on phenom/radeon 4870"
date: 2009-01-27
forum: Hardware
---

### Post by jc87 on 2009-01-27
I want to install Ubuntu 8.10 on my new machine, i start booting the live-cd but after the progress bar the screen goes black and i can´t do anything at all (tried alt plus f4 to try go CLI, also control plus alt plus backspace, but still just black)

If i boot in safe graphics mode it works like a charm, and i can run the live-cd.

Now if i install at safe graphics mode, will the installation use the VESA mode as default when i boot from the disk? If not how can i force it to use it, or have it install the fglrx driver right away? 

I´m thinking about mounting the / from the live-cd (right after finishing installing it) and edit the xorg.conf to use the Vesa driver ( does the xorg version shipping with 8.10 still uses a xorg.conf ???)

I´m afraid of installing and ending up with a install that does nothing because the screen just goes black, so that is the reason why i asK.

I tried with 8.10 32 bit, also with the latest 9.04 alpha ( same graphics problem).

My machine is an AMD Phenom 920, 4 gigs of ram, radeon 4870 1 gig GDDR5 from powercolor, mobo DFI Lanparty DK 790GX-M2RS

Thanks in advance

---

### Post by Vahids on 2009-10-02
I have same problem,
AMD Phenom II 720 X3
ATI 4870 1G

---

### Post by markbuntu on 2009-10-02
The problem you are having is that the Intrepid iso is borked as far as fglrx goes. The best thing woul be to install in safe graphics mode and then install the latest driver from the ati site. Intrepid will only be supported for another 6 months. You might be better off waiting a few weeks and installing 9,10 instead. It has a driver that will work with your gpu OOB.

---

### Post by Vahids on 2009-10-05
> **markbuntu said:**
> The problem you are having is that the Intrepid iso is borked as far as fglrx goes. The best thing woul be to install in safe graphics mode and then install the latest driver from the ati site. Intrepid will only be supported for another 6 months. You might be better off waiting a few weeks and installing 9,10 instead. It has a driver that will work with your gpu OOB.
Thanks man!
driver 9.9 work like charm! and i'm happy :)

---

