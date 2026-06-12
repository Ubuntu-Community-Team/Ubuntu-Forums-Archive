---
title: "New Dell Inspiron 15 5567: Compatible?"
date: 2016-12-29
forum: Hardware
---

### Post by Starbeamrainbowlab on 2016-12-29
Hello,

You've probably seen a million of this type of post already - I think this is the right place to put it (please let me know where else I should put it if not here). I'm looking to get a new laptop, and I've found a Dell Inspiron 15 5567 that I'm thinking of buying. Obviously, the question is whether it'll run Ubuntu.

Link: [http://www.dell.com/uk/p/inspiron-15-5567-laptop/pd?oc=cn55707&model_id=inspiron-15-5567-laptop](http://www.dell.com/uk/p/inspiron-15-5567-laptop/pd?oc=cn55707&model_id=inspiron-15-5567-laptop)

It apparently comes with an AMD Radeon™ R7 M445 Graphics 4G GDDR5 dedicated graphics card. Here are my questions:


[LIST]
[*]Does it run Ubuntu?
[*]What should I watch out for? (I'm coming from an Inspiron N5110, with no UEFI. I've heard UEFI can cause problems)
[*]Will the dedicated graphics card work? How does it work (e.g. how do I get things to run on it? does everything, or just selected programs run on it?) Currently my laptop has an Nvidia 525M, but I can't get it to work with Ubuntu :-(
[*]Which drivers would I need to install to take full advantage of the hardware in this laptop?
[/LIST]

Regards,
Starbeamrainbowlabs

---

### Post by TheFu on 2016-12-30
The only way to know with an Inspiron is to buy it and load Ubuntu.  They swap out parts as needed during production, so even if someone else has the same machine, it may not have the same config as yours. The best you can do is look at all the chips involved and research each 1 individually for Linux compatibility.  I'd be worried about the wifi, bluetooth, and GPU mostly, but really new CPUs have had issues recently too.  Skylake. Don't think they have all those issues resolve yet.

95% of the time, unless it is a very new MB/CPU, everything will be fine. The GPU support is different. You'll need to check that separately. To avoid all that, I just use IGP with the Intel CPUs. My last AMD GPU doesn't work well with Linux anymore. It worked fine for my uses when it was newly installed, but the GPU was an older Radeon and support was dropped by AMD.  Barely use any of my nVidia GPUs anymore. They are in headless systems.

If you want 100% pre-knowledge, then get a computer that someone has with exactly the same chips (southbridge/northbridge/cpu/GPU/ethernet/wifi/disk controller/usb controllers/etc) involved.  For most people, that means buying a computer that has a known, unchanging, config. Apple, Dell business, etc.

I've owned a few Dells over the years. Still have a Dell Inpiron Core i5 that ran Ubuntu fine, last time I booted it into Linux.  Wifi, ethernet, GPU, CPU, everything worked as expected. It is about 6 yrs old now and the keyboard has been repeating at boot for about a year. Takes some time to get that to stop. Funny thing is - the laptop hasn't moved in years and it is treated like a desktop replacement - connected to external keyboard, mouse, audio, and dual monitors. The onboard keyboard, touchpad and monitor aren't used and haven't been most of the time I've owned it.  

For me, a powerful laptop isn't something I plan to ever own again. Using a chromebook with Ubuntu loaded now and use that to remote into much more powerful systems as needed. A $400 desktop easily beats a $2000 laptop in performance, plus all the expansion and easy-to-swap components make it a clear choice for me. 

But we all have different requirements based on our needs. I don't need fast local graphics. Maybe you do.

Did some googling. Didn't find anyone saying this did or didn't work. However, didn't see any of the chips listed either.  I'd be cautiously optimistic. Dell would be my first choice, actually, but I'd start with the XPS 13. High resolution. Lighter. Longer battery.  I'd also look at a few Asus models.  I'm prejudiced against Lenovo, Acer, Toshiba and HP for a number of reasons. HP for technology and pasted "screwing" (bought lots of HP equipment over the years at work, mostly Unix systems) and Lenovo for adding spyware, back doors, to their hardware. Acer for terrible build quality; power plug replaced 3 times on 2 different devices and a number of issues on a C720 (it is bricked now). Toshiba for terrible warranty support (claimed a broken screen was my fault when it was carefully babied prior to the break).  The issues I've had with Dell were all my fault, I've had a few. Not build quality. Was able to get cheap replacement parts where that made sense. I don't expect laptops to last forever either, but I'm very gentle and do expect 4-6 yrs from a laptop that travels 3-4 times a year and is home-bound the rest of the time.

OTOH, my desktop/servers have been working 24/7/365 for 6+ yrs now. Only issues were dust/cooling and loose cables due to vibration. 

As for drivers - the easiest, best, support comes from selecting devices that have direct Linux kernel support. When components are used without that support (new stuff), then all bets are off.  Getting last years model is the way to have more assurance on compatibility.

Or I could be completely wrong. Don't own this specific laptop, so don't know.

---

### Post by Starbeamrainbowlab on 2016-12-31
@TheFu Thanks for your detailed insight! Unfortunately, a desktop isn't currently an option (not enough space), but if it were possible I'd rather like one.

I think I'll go for it anyway (it is listed on [this page]("https://support.amd.com/en-us/kb-articles/Pages/AMD-Radeon-GPU-PRO-Linux-Beta-Driver%E2%80%93Release-Notes.aspx#") after all) - I'll report back once it's installed & set up for the benefit of future users.

---

### Post by Starbeamrainbowlab on 2017-01-19
I'm back! Thankfully, I've had almost no trouble at all with it :D

The only minor issue I've got is a slight flickering in chrome sometimes, but that's totally bearable considering the frequency.

The annoying thing is that the AMDGPU-Pro driver causes a kernel panic when I'm logging in, but I haven't managed to save & analyse a crashdump yet. That's another story though - I'll make another post about that if I continue to experience issues.

---

### Post by linuxguiri on 2017-02-25
I haven't been so lucky with my Inspiron 15 5567. Internet keeps dropping randomly on both wired and wireless connections, but the connection icon says its still connected. I have to disconnect and reconnect to reset it constantly. You didn't have that trouble?

Also, it won't wake from suspend. Not a problem for you?

(I get that flickering in Chrome as well, but as you say, it's bearable). 

I filed a bug for the internet issue here: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1666432](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1666432)

---

### Post by lukas522 on 2017-07-21
Hi, I have a Dell with the same graphics card and i have the same issue (well, same machine 5567). I wanna make the graphics work but unsuccessfully and the only option i have is login into text mode and uninstall the driver to go back into graphical mode after reboot.

Did you solved it? and if your answer is Yes, tell me how.

---

