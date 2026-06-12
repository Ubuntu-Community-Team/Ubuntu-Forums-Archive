---
title: "Windows to Ubuntu programs?"
date: 2008-09-26
forum: General Help
---

### Post by azTom on 2008-09-26
I'm relatively new to Ubuntu and would like advice on a recommended program that will transform Windows programs to Ubuntu.  Some financial programs I have require IE to work.

Thanks for any and all help/advice.

---

### Post by DrMega on 2008-09-26
If you install WINE (which is in the repositories) you will be able to run many (but not all) Windows applications on your Ubuntu machine.

Other than that, you can't convert apps from Windows to Ubuntu, but in the case of open source ones you might be able to find Linux versions.

---

### Post by azTom on 2008-09-26
Thanks, but I've been told there are a few programs (not FREE) that are easier to use than Wine.  Wine I've been told is not very easy to set up.  I've been told the paid programs transform many Windows programs to Ubuntu via setting-up Wine.

Thanks for your prompt reply.

---

### Post by Sycron on 2008-09-26
Is not hard to set up. Just try it.

---

### Post by DrMega on 2008-09-26
> **azTom said:**
> Thanks, but I've been told there are a few programs (not FREE) that are easier to use than Wine.  Wine I've been told is not very easy to set up.  I've been told the paid programs transform many Windows programs to Ubuntu via setting-up Wine.

Thanks for your prompt reply.

Would the people that told you that be the same people that sell these non-free alternatives by any chance?

When I installed WINE I just chose it from the repository. I didn't configure anything manually, I just installed it and it worked.

---

### Post by Sycron on 2008-09-26
I can confirm that too. No extra configuration was needed.

---

### Post by brookswm on 2008-09-26
> **DrMega said:**
> Would the people that told you that be the same people that sell these non-free alternatives by any chance?

When I installed WINE I just chose it from the repository. I didn't configure anything manually, I just installed it and it worked.

Same here, installed Wine and started playing WoW, easy as pie.

---

### Post by Sycron on 2008-09-26
Well that's the FUD, no ?

---

### Post by DrMega on 2008-09-26
> **azTom said:**
> Some financial programs I have require IE to work.

Sorry I didn't notice this bit in your post. I don't think anything in Linux will get IE to run properly.

However, there may still be a simple solution. FireFox can do everything that IE can but the DOM has some slight differences, and some apps expect IE as the client. There is an agent changer addon for FireFox that tells it to report itself as being IE. Some stuff that expects IE accepts this. You could give it a try. Sorry I can't tell you what the addon is called because I've never used it, but a quick visit to google should find it for you.

---

### Post by russlar on 2008-09-26
> **DrMega said:**
> Sorry I didn't notice this bit in your post. I don't think anything in Linux will get IE to run properly.

However, there may still be a simple solution. FireFox can do everything that IE can but the DOM has some slight differences, and some apps expect IE as the client. There is an agent changer addon for FireFox that tells it to report itself as being IE. Some stuff that expects IE accepts this. You could give it a try. Sorry I can't tell you what the addon is called because I've never used it, but a quick visit to google should find it for you.

I believe the add-on is called "User Agent Switcher"

---

### Post by kokkus on 2008-09-26
FIrefox can't do everything IE can do. like what about ActiveX?

---

### Post by DrMega on 2008-09-26
> **kokkus said:**
> FIrefox can't do everything IE can do. like what about ActiveX?

That's not a limitation of FireFox. ActiveX is a Windows specific technology. The Windows version of FF will run ActiveX controls if you enable it to (it is disabled by default because ActiveX on web pages is one of the easistes ways for malicious code to circumvent security on a Windows PC).

---

### Post by kokkus on 2008-09-26
So theres no way to get activex on ubuntu?
I mean, sometimes u need activex

---

### Post by Sycron on 2008-09-26
I never needed activeX on ubuntu.

---

### Post by russlar on 2008-09-26
> **Sycron said:**
> I never needed activeX on ubuntu.

I never needed activex on windows, either.

---

### Post by Sycron on 2008-09-26
We'll in the past, when I was a pure M$ fanboy haxor I were using activeX to install a RAT at school's computers. So much fun...

Now I know it's illegal and I stopped doing that. :)

---

### Post by kokkus on 2008-09-26
Sometimes activex is great. when it comes to p2p streamed TV.
Sopcast, TVU Player, TVKoo etc. if you are familiar with that.

---

### Post by DrMega on 2008-09-27
> **kokkus said:**
> So theres no way to get activex on ubuntu?

No idea. I've never tried. This is a good question on its own, why not start a new thread asking this question? I'm sure someone knows.

---

