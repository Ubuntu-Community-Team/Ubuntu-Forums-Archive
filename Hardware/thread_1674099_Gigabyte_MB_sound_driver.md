---
title: "Gigabyte MB sound driver"
date: 2011-01-23
forum: Hardware
---

### Post by OZZ_ on 2011-01-23
I recently acquired some odds and ends and put together a PC out of it that Im currently using to post this. Dual core Intel pent. D @ 2.8ghz, 1 gig DDR 400, 500G SATA wd and a Gigabyte GA-8I865-775 motherboard.

Works pretty good for a general purpose PC. Im running ubuntu 10.04 LTC and I cant seem to get the sound to work. Gigabyte does not list any linux drivers for the board, and I havent been able to dig any up as of thus far. Ive installed this version of ubuntu on four different PC's recently  including two different laptops and the included sound drivers always  seemed to work out of the box. So partly, Im almost wondering if theres something wrong with the sound on the motherboard itself, although I certainly cant make that conclusion from what Ive got at hand.

Can anyone point me in the right direction for a linux audio driver that might work on this board? Its an older board so Im really surprised the packaged drivers dont work out of the box.

Any help is appreciated! Im new to linux. I did download sysinfo and it lists my audio controller as **: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)**

After doing a little digging around it seems others have no audio as well with this controller.

The command aplay -l gives me the following:

**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Im very green to linux, as in Ive been using it for barely two weeks, always used windows before. This seems to me like it is seeing the audio card? Would you agree?? If so, Im not sure what the hang up is unless I just need a different driver. Im not sure where to go from here??

Any thoughts?

---

### Post by Aprilpaul on 2013-01-04
Hi, Interested in this issue as I have the same problem. Its now 2 yrs later, and a newer version of Ubuntu  (12.10) , but I cant get the sound card to work.

I cant find anywhere to look to see if I could load a new driver or search for the audio card.

I was interested if you had found a resolution?

---

### Post by Yellow Pasque on 2013-01-04
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by overdrank on 2013-01-04
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

