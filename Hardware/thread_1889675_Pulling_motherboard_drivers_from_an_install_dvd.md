---
title: "Pulling motherboard drivers from an install dvd?"
date: 2011-12-01
forum: Hardware
---

### Post by Los Frijoles on 2011-12-01
So, I have just finished the hardware portion of my first me-built computer. I have installed Ubuntu 11.10 64-bit and I am using an Intel i5-2500K processor. At the moment I have found a solution to most of my issues except the sensors on the motherboard. I have an ASRock Z68 Pro3-M which according to my googling doesn't support lm-sensors (and after trying it out it really doesn't). I have the motherboard install DVD (which is for windows) and I am now in the process of installing WINE to run the setup to see what will happen.

However, I really don't think wine is going to work so my question is: How can I get sensors working with an ASRock Z68 Pro3-M motherboard? Can I pull the drivers off the dvd? Do I have to write my own drivers (its not out of the question...sooner or later I have to learn how (haha what a first driver dev project that would be))?

Also, random question...I am not sure the integrated graphics are indeed working...does ~40fps in Nexuiz generally mean it is working (I know it's a stupid question...but I really have no experience in graphics stuff and for all I know the cpu alone is doing that)?

Thanks in advance.

---

### Post by bluexrider on 2011-12-01
this review may help you [http://www.phoronix.com/scan.php?page=article&item=asrock_z68_pro3&num=1](http://www.phoronix.com/scan.php?page=article&item=asrock_z68_pro3&num=1)

---

### Post by Mark Phelps on 2011-12-02
If your question is can you use Wine to install Windows drivers, the answer is NO. With the rare exception of NDISWrapper, Windows drivers do not work in Linux.

---

