---
title: "Can beryl be used on ubuntu"
date: 2008-07-29
forum: General Help
---

### Post by broivan on 2008-07-29
How can i use beryl or compiz fusion is it availabe. And when i change the setting to advanced graphics it my pc does not support it. Do i need a more advanced graphics card.

---

### Post by scragar on 2008-07-29
System>Preferences>Appearance

go to the "Visual Effects" tab, turn it on. That's compiz fusion.

If you get a message saying it can't be turned on it could be a requirement for a better graphics card, or you may just need to update the driver. post your graphics card name back here, I'll see what I can pull up about it.

---

### Post by ibuclaw on 2008-07-29
It is called [Compiz-Fusion]("http://www.compiz-fusion.org/"), and yes, Ubuntu has supported it for quite a while.

What is your Graphics Card?
```
lspci | grep VGA
```

You can get the most core components from the repository:
```
sudo apt-get install compizconfig-settings-manager emerald fusion-icon
```

Then press **Alt+F2** and type in "fusion-icon", and a blue cube applet will appear in the top-right hand corner of your screen.

From there, you can set your window manager/compiz effects.

Regards
Iain

---

### Post by steveneddy on 2008-07-29
Beryl is not supported anymore and has integrated with Compiz Fusion.

---

### Post by bodhi.zazen on 2008-07-29
I do not know if it will help, but you can check this out :

[http://forlong.blogage.de/article/pages/Compiz-Check](http://forlong.blogage.de/article/pages/Compiz-Check)

---

### Post by sailor2001 on 2008-07-29
Edgy was the last to use beryl......

---

### Post by armageddon08 on 2008-07-30
> **sailor2001 said:**
> Edgy was the last to use beryl......

Well...I'm still using it on Hardy.

---

### Post by billgoldberg on 2008-07-30
> **armageddon08 said:**
> Well...I'm still using it on Hardy.

Why?

---

### Post by armageddon08 on 2008-07-30
> **billgoldberg said:**
> Why?

Actually..I have both. There some effects on beryl which CF does not have e.g. the window ripple effect. Also beryl seems to work better than CF an my box. The animations seem smoother, the curves seem better....I find it more stable.:)

---

### Post by steveneddy on 2008-07-30
> **armageddon08 said:**
> Actually..I have both. There some effects on beryl which CF does not have e.g. the window ripple effect. Also beryl seems to work better than CF an my box. The animations seem smoother, the curves seem better....I find it more stable.:)

You aren't the only one lately to say that.

---

### Post by armageddon08 on 2008-07-31
> **steveneddy said:**
> You aren't the only one lately to say that.

Well....are you talking of that 'Beryl works better than Compiz' thread. Don't get me wrong. I'm not blaming the CF devs.....I was just sharing my personal experience:neutral:

---

### Post by steveneddy on 2008-08-01
> **armageddon08 said:**
> Well....are you talking of that 'Beryl works better than Compiz' thread. Don't get me wrong. I'm not blaming the CF devs.....I was just sharing my personal experience:neutral:

I have experienced what you speak of and I agree with you on many points, but it is so buggy and crash prone that I can't make myself go back to it.

Beryl did do some eye candy things better that CF does now.

I will wait on David to see what he comes up with, but I just wish Kristen would get her old code back into CF, then we would have a k-a CF.

Get 'er done!

---

### Post by armageddon08 on 2008-08-02
> **steveneddy said:**
> I have experienced what you speak of and I agree with you on many points, but it is so buggy and crash prone that I can't make myself go back to it.

Beryl did do some eye candy things better that CF does now.

I will wait on David to see what he comes up with, but I just wish Kristen would get her old code back into CF, then we would have a k-a CF.

Get 'er done!

Well....Beryl does not crash on my box....dunno why.....but that's good. 
Let's hope we have a really good and stable WM in CF to challenge the likes of Aero and Aqua.:)

---

### Post by steveneddy on 2008-08-02
> **armageddon08 said:**
> Well....Beryl does not crash on my box....dunno why.....but that's good. 
Let's hope we have a really good and stable WM in CF to challenge the likes of Aero and Aqua.:)

I don't guess that I've used Beryl since Feisty, but I truly enjoy CF now.

---

### Post by armageddon08 on 2008-08-02
> **steveneddy said:**
> I don't guess that I've used Beryl since Feisty, but I truly enjoy CF now.
I switch to CF sometimes when I just wanna show-off absolute eye-candy. Otherwise for daily work I use Beryl which seems to have no probs but one-- emerald doesn't work.

---

