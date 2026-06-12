---
title: "Should I take proprietary driver?"
date: 2010-04-06
forum: Hardware
---

### Post by leonardo_neo on 2010-04-06
Recently bought Acer Aspire 5517, AMD processor, and installed Ubuntu 10.04 64bit.

Everything is fine, except the external mic is not working properly. (There is no internal mic)

When I check the available "hardware drivers" offered, I see ATI/AMD proprietary FGLXR graphic driver available to use. Screen shot attached.....

When I run "lspci -nn | grep VGA" command to check my computers graphic driver, I get this output....

> 01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] [1002:9612]

So here is my question....

1. Should I try the ATI/AMD FGLXR driver offer by the driver manager?
2. If I try the driver offered and if it doesn't work, will I be able to remove that by unchecking the box? I mean will I be able to have everything as it was before this trial?

I am scared to do experiments with my drivers, so I am asking this question.

Thanks in anticipation.

---

### Post by lrgmmc on 2010-04-06
Those drivers are for your video. ie better 2d and 3d. so yes i would install them. and of cource you can remove them if you are not satisfied, but i doubt you will.

---

### Post by leonardo_neo on 2010-04-07
> **lrgmmc said:**
> Those drivers are for your video. ie better 2d and 3d. so yes i would install them. and of cource you can remove them if you are not satisfied, but i doubt you will.


Thanks for the advice......I installed them everything seems to work fine, except for the splash screen before login window, which didn't pick up the right resolution.(It doesn't bother me though)

The proprietary drivers seems to work better than the open source one, but is there any benchmark tool to measure the actual performance of both the drivers? I mean it could be my subjective perception as well?

Thank you all again for your help.

---

### Post by vie et mort on 2010-11-03
I was wondering how your Proprietary Driver has been holding up and whether or not you found a way to fix your external mic problem.

---

### Post by leonardo_neo on 2010-11-04
> **vie et mort said:**
> I was wondering how your Proprietary Driver has been holding up and whether or not you found a way to fix your external mic problem.

I have install 10.10

The proprietary driver works great, except for the shaky splash screen.

The external mic problem in Acer aspire 5517 is still not fixed. The bug has been reported long time ago.

---

