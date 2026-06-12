---
title: "Duel graphics card settings"
date: 2020-01-29
forum: Hardware
---

### Post by jd8788 on 2020-01-29
I am hoping to find someone or some people to help me configure setting for dual Radeon 7000 series graphics cards for optimal fps during gameplay. I have installed the second card and notice no difference in gameplay and sometimes from into the 40s range in fps only playing Terraria . I am running Ubuntu 18.04 with two Sapphire Radeon HD7870, AMD FX 8750 processor with 2x 8 GB Kingston ram 1333 MHz DDR 3.

---

### Post by Yellow Pasque on 2020-01-30
Sorry, but Crossfire(X) doesn't work on Linux. Even when ATI/AMD tried to support it in their proprietary driver years ago, it only worked with a handful of OpenGL games/apps.
Programs that use Vulkan may be able to make use of multiple GPU's, but it is up to the developer to make that work, rather than configuring it at the OS/driver level.

---

### Post by jd8788 on 2020-01-30
Okay thank you, it seems you are correct. I have received the same response on another forum. On that note, is there anything you can recommend to increase fps? I have room to overclock but am a novice and the files to change hardware parameters is still hard for me to completely understand. I am currently only playing Terraria and when running on Windows I can get 60fps . I just can't stand Windows:)
 Also I should note, I'm running the Radeon drivers not amdgpu.

---

### Post by Yellow Pasque on 2020-01-30
I can't explain the performance difference between Win and Linux, but I'm unfamiliar with the game. Maybe you're better off asking on Terraria tech support forums?

> I'm running the Radeon drivers not amdgpu. 
Performance is fairly close between the two: [https://www.phoronix.com/scan.php?page=article&item=amdgpu-radeon-linux50&num=1](https://www.phoronix.com/scan.php?page=article&item=amdgpu-radeon-linux50&num=1)
As the article notes, the main benefit of amdgpu is allowing Vulkan support. That's not relevant to your issue, since Terraria uses OpenGL.

> I have room to overclock
I think you're headed down the wrong road there. OC'ing probably isn't going to take you from 40fps to 60fps. It may get you a few fps.

---

### Post by CelticWarrior on 2020-01-30
> **Yellow Pasque said:**
> I think you're headed down the wrong road there. OC'ing probably isn't going to take you from 40fps to 60fps. It may get you a few fps.

**+1**

The sad reality is, in this case, the game's versions for Windows and Linux, albeit both native, cannot be compared. The Windows version uses DirectX and the Linux port uses OpenGL. This alone can account for the difference in performance, everything else being equal (and everything else seldom is with this ports being an afterthought).

---

### Post by jd8788 on 2020-01-30
Thank you this has been very helpful. I do want to say most of the game will run around 55fps and I do see 60 here and there but anytime there's a few extra things going on it quickly drops down. That is why I was thinking maybe to overclock. Although my graphics card is also Sapphire and overclock by them. I appreciate your help and feel satisfied with the information contributed. I have one more thought. Is there other possibilities including different hardware that uses is generally better for gaming on Linux. I assume upgrading hardware is first to thought, but I rather mean better performing drivers made more so for linux, such as Invida it something.

---

