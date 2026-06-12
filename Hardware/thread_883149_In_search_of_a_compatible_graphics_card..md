---
title: "In search of a compatible graphics card."
date: 2008-08-07
forum: Hardware
---

### Post by OlaNordmann on 2008-08-07
Well; I can only say that I've been quite unfortunate with my recent cards, and I'm really getting sick of it.

Simpler/generic drivers won't support dual monitors (can't probe secondary output with my cards) so i have to resort to proprietary software. And it's getting on my last nerve. I don't want to recompile drivers after each kernel upgrade.... The newest card I installed won't even work. I've tried binary repositories, envy, official drivers, any guides I've come across; and it still won't work. Not to mention the fan is extremely loud.

So instead of pulling out more hair, I want to invest in another card. with very simple criteria: 
[LIST]
[*] I want my hardware to be open and functionally out-of-the-box. Meaning I don't want to rely on special set of drivers. 

[*] I would need two DVI outputs (expanding X over two monitors).

[*] Is capable of running a resolution of 1680 x 1050

[*] Preferably a cool/quiet low-budget card, I'm not much of the gamer type, but rendering HD-films should definitely be doable :)
[/LIST]

Please Ubuntufolks, I need your help :KS

---

### Post by phidia on 2008-08-07
Sounds like you've had a lot of trouble. Really sorry to hear that.
Intel integrated cards seem to set up pretty well in linux but I don't think they make a discrete video card (a card you can plug into to an AGP or PCI-e slot)
I also think it would be very hard to find a budget card with two DVI outputs.

So if you want to go the way you say you do you might want a new motherboard or computer with an integrated video card.

I don't know if you asked for help with your current card, but there might be a way to get it working. I do understand it can be very frustrating. 

I'm going to provide a link to the [Ubuntu video wiki]("https://help.ubuntu.com/community/Video") and hope you find something that works for you.

Added: I'm not sure if your present card is ATI or Nvidia anyway there is a silent 9600 nvidia card [here from newegg]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814121244"). It uses a massive heatsink and no fan-so no noise from the card at least.

---

### Post by OlaNordmann on 2008-08-08
Hey phidia ):P
I was really glad to come home and see someone who replied to my thread.

Well ok, I decided that I don't want another ATI/Nvidia GPU, and that I've wasted enough time trying to get this one too work.

Correct me if I am wrong, but i think Intel only makes embedded graphics processing in motherboards, instead of seperate retail cards. 

But I've been looking in to the alternatives though I don't know enough about it. Matrox seems to make cards that I'm looking for; simplier specifications with dual dvi's. Most of them also have preinstalled heat- pipes/sinks which is a big plus. But the compatibility is the one thing I'm concerned about. Most only have 32-128 MB of memory.. Do you think video playback is going to work flawlessly?

---

### Post by phidia on 2008-08-08
Yes you are right intel only makes integrated (embedded) graphic chips. That's why I said a new motherboard could be an option-maybe.

I don't know that much about Matrox, but the thing about helping is I get to learn more :) Wikipedia has a whole history and specifications about them [here]("http://en.wikipedia.org/wiki/Matrox_G400"). Be sure to look at the complete write up there is a lot there. I am not sure how complete linux support is for matrox.

This is probvably not a good thing for me to suggest _here_ but did you ever consider trying a different distro? [Sabayon]("http://www.sabayonlinux.org/") has it's flaws too, all distros do, but it sets up video and a lot of video related features automatically.

---

### Post by TrendRat on 2008-11-12
Hello OlaNordmann

I hope I'm not to late with my post - please do NOT I repeat do NOT switch to a Matrox card for an Ubuntu machine!!!!  I've had a Matrox Parhelia 128MB AGP 4x card in my machine for some time - it's a major pain to get up and running.  Matrox does not provide any driver updates for Ubuntu, and you have to get them from an unofficial source ([http://forum.tuxx-home.at/index.php](http://forum.tuxx-home.at/index.php)).  

I had mine running well on Ubuntu 8.04 (after much pain!), and decided to upgrade to 8.10.  Rather than mess with the Matrox card, I am replacing it with an nVidia 7600GS.

Good luck,
TrendRat

---

