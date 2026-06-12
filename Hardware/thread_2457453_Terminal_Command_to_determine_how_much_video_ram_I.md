---
title: "Terminal Command to determine how much video ram I have"
date: 2021-02-02
forum: Hardware
---

### Post by bobnutfield on 2021-02-02
Hello Everyone

I have an old laptop that i want to do some video editing with, using the most powerful software my laptop will handle.  I know I can use some lighter editors like Openshot, but I wanted to try get a little better.  I don't want Lightworks because it will only render in 720p if you use the free version (I don't do it enough to pay for a subscription.)  Ideally, I wanted to use DaVinci Resolve, but I know this laptop won't handle it.  I'll probably use Cinelerra GG if this laptop will handle it without using proxy files, plus the video is from my drone which shoots in 4K.

I am sure this old thing has integrated Intel graphics, so it won't have much in the way of video ram, but I want to find out what it is,  the lshw command does not give me that information.

Is there a terminal command that will fully describe the graphics, including video ram?

I appreciate any replies

Bob

---

### Post by CelticWarrior on 2021-02-02
There's no video RAM *per se* with integrated graphics. It's shared, i.e., reserved from the system's RAM and how much it's used is defined by BIOS/UEFI if such settings is available, of course.

---

### Post by bobnutfield on 2021-02-02
Thanks, CelticWarrior

I was afraid of that because there is no setting in the BIOS to adjust what is shared.  Nothing to do but just try it, I guess and see the results.

Thanks again

Bob

---

### Post by CelticWarrior on 2021-02-02
If you know how much physical memory you have then you can check how much memory is available at Settings > About.
The difference is roughly the reserved VRAM. Roughly because a small part is assigned for other system usages other than video. So, the actual VRAM is slightly less than that difference.

---

### Post by bobnutfield on 2021-02-02
Thanks, CelticWarrior

I was afraid of that because there is no setting in the BIOS to adjust what is shared.  Nothing to do but just try it, I guess and see the results.

Thanks again

Bob

---

### Post by bobnutfield on 2021-02-02
Thanks again.  According to that, there is only about 300mb going to VRAM.. Not much.  But, Cinelerra GG seens to run fairly well.  I can't afford a higher end laptop right now (spent too much on the drones), so it will have to do.  I have 8GB if RAM installed and 7,700mb available.  I assume the rest is going for graphics.

Bob

---

### Post by rsteinmetz70112 on 2021-02-02
You could add more RAM to the laptop, that will usually recalibrate the amount shared.

---

### Post by bobnutfield on 2021-02-03
> **rsteinmetz70112 said:**
> You could add more RAM to the laptop, that will usually recalibrate the amount shared.

Thank you, but I've already added to the max of 8GB.  This old laptop runs amazingly to be so old, but the editing software I want to use requires a minimum of 2GB of dedicated memory to run.

I'll just have to settle with a less demanding editor.

Bob

---

