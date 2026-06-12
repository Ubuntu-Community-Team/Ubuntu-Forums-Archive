---
title: "Ubuntu 13.04 and Lenovo ThinkPad S431?"
date: 2013-08-13
forum: Hardware
---

### Post by CaptSaltyJack on 2013-08-13
Anyone have any personal experience running Ubuntu 13.04 (or later) on the ThinkPad S431? That laptop is at a really nice price point and is powerful enough for what I want it for. Thanks in advance.

---

### Post by CaptSaltyJack on 2013-08-14
Ok maybe not. I guess I'll take a risk and be a pioneer. :)

---

### Post by Boab1993 on 2013-08-14
I dont have any personal experience on the product but it has been given the ubuntu 'enabled' status for 12.04 LTS.

13.04, i would not know, sounds like your going to be a pioneer.

You can find information on the product certification here : [http://www.ubuntu.com/certification/hardware/201305-13524/](http://www.ubuntu.com/certification/hardware/201305-13524/)

Hope this helps.

---

### Post by CaptSaltyJack on 2013-08-14
Saw that. It was tested for 12.04 and passed. What does "enabled" mean, vs "certified"?

---

### Post by Boab1993 on 2013-08-14
I think enabled means it has the basic ability to run ubuntu. So it can run the OS, but is not guarenteed to have all features working/bug free.

Certified means that it should -in therory- run seemlessly on your system with no or minimal bugs.

They will have official definitions on their site somewhere if you want more details.

---

### Post by CaptSaltyJack on 2013-08-14
Thanks!

---

### Post by Boab1993 on 2013-08-14
Post your findings if you choose to upgrade by the by, can't help to have a bit more information on things

---

### Post by CaptSaltyJack on 2013-08-14
S431 ordered! I will report here. If there's another official place I should report, let me know.

---

### Post by connors2647 on 2013-08-27
> **CaptSaltyJack said:**
> S431 ordered! I will report here. If there's another official place I should report, let me know.

Did you get the S431 yet? I am interested in buying a lenovo also but want to be sure Ubuntu can run on it.
Did you install 13.04? or 12 LTS?

---

### Post by CaptSaltyJack on 2013-08-27
Arrives tomorrow! Can't wait. I'll be installing 13.04 on it. I'll be sure to come back here and post once I get it installed and have used it for a week.

---

### Post by connors2647 on 2013-08-27
I can't wait till you let me known if it installs fine. I have my mouse pointer on the Buy Now button in Ontario Canada

---

### Post by connors2647 on 2013-08-27
Oh yeah. I want the same model you ordered, S431

---

### Post by CaptSaltyJack on 2013-08-28
BEAUTIFUL laptop! Love it. I kinda wish it had some indicator lights (for caps lock, HD activity, etc). The dot on the 'i' in ThinkPad does light up though. :) It does this when the machine is on, and it indicates when the machine is asleep.

Ubuntu 13.04 installed with zero issues. Popped in the USB drive, rebooted, kept hitting F12 to bring up the boot menu. Out of the box, everything works great except the brightness keys. I had to follow the instructions here to fix it:

[http://askubuntu.com/questions/298655/lenovo-l430-malefunction-brightness-control-13-04](http://askubuntu.com/questions/298655/lenovo-l430-malefunction-brightness-control-13-04)

Screen is fantastic (matte). Gotta get used to the placement of the Fn key (it's where I'd expect Ctrl to be). Keyboard is great, trackpad is excellent.

Also be sure to install the tlp tools (then reboot):

sudo add-apt-repository ppa:linrunner/tlp
sudo apt-get update && sudo apt-get install tlp tlp-rdw

This will give you optimal battery use. This really applies to any laptop install of Ubuntu.

Oh PS: sleep mode works perfectly on this machine, unlike most laptops where you try to wake it up and it won't.

---

### Post by CaptSaltyJack on 2013-08-28
Oops. It won't shut off. :) I do shutdown, it turns off, then turns back on. Ok, so.. a few kinks. I'm sure this is all fixable though.

---

### Post by connors2647 on 2013-08-28
Ah thats Great news. 
A few Questions:

1. Did you do a clean wipe and install of 13.04? Thats what I plan on doing.
2. Which model did you get?
59372990 - 4GB RAM, 500GB HDD
59372987 - 8GB RAM, 500GB 5400RPM+24G SSD (this is what I am worried about the SDD)
or the BIGGIE - 59372999 - 1TB HDD

Im gonna ask the wife if I can order mine tonight! Ill let you know how it goes.
Thanks alot. Hope you solved the shutdown issue.

---

### Post by CaptSaltyJack on 2013-08-28
Shutdown kinda fixed itself. All is well! The trackpad is a little jumpy sometimes when tapping to click. I'm gonna see if I can fine tune it. And yes, I did a total wipe and installed 13.04 64-bit from scratch.

---

### Post by connors2647 on 2013-08-28
Ok. Great. My wife and I agreed to order it Now! Which one did you get again? I am concerned about the 24GB SDD on middle model.

I prefer to use a wireless mouse, can you turn off the trackpad?

---

### Post by CaptSaltyJack on 2013-08-28
You can turn off the trackpad in the system settings. I went with the i5 CPU, 4GB RAM (since you can expand it yourself later), 128GB SSD.

---

### Post by connors2647 on 2013-08-28
I have been looking for another model with HDMI input capabilities

---

### Post by connors2647 on 2013-08-29
Just ordered the S431 before the sale deadline at midnight! Should be delivered by Sept 5 2013

Qty	Part no.	Description	Status	Price	Total
1	20AXCTO1WW	ThinkPad S3-S431 Intel $747.12	$747.12

Subtotal	$747.12
Environmental Handling Fee	$1.50
Tax (G.S.T./H.S.T.)	$97.32
Tax (P.S.T./Q.S.T.)	$0.00
Total	$845.94

---

### Post by connors2647 on 2013-08-29
Lol. Just checked Lenovo website. Sale is extended till Sept 2. They got me to make a rush purchase! Lol

---

