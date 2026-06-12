---
title: "Does Sabayon have good support for 64 bit?"
date: 2007-01-13
forum: Gentoo and derivatives
---

### Post by raul_ on 2007-01-13
This is probably a question for RAV TUX since he seems to make a lot of posts about Sabayon. I'm really interested in Sabayon Linux, the only thing that keeps me from changing is that I don't have much space left in my drive, and although i know it works with Gnome too, i don't like KDE at all.Oh, and i'm kinda lazy with the fact that i'll have to get used to Portage :mrgreen:
  But one of the things that bug me in Ubuntu is that the 64bit version doesn't seem to be that good. I haven't tried it, but i read a lot of posts, and it seems that who tried, didn't stick with it for long. It's not really a big deal because it works fine with the 32bit version, but i can't stop from thinking that maybe i could boost the performance (which, again, is already very good) with a 64bit OS. 

Could someone shed some light on this? :rolleyes:

---

### Post by Rodneyck on 2007-01-13
I don't know if that is necessarily an Ubuntu thing or just hiccups in the 64 bits and linux. I get conflicting reports from various distros.

Regardless, it will be a faster option, but there are a few apps and plugins that are not compatible with the architecture. Websites usually use a lot of flash these days and flash pluggins and 64bit are currently incompatible from what I have read. There are other hiccups as well, just do a search on this forum and others. The only way to find out is try the liveCD for sure and do your research and weigh the trade off for yourself. It depends on how you use the computer.

I agree with the portage comment, it is no debian apt-get. Upgrading, which is mostly discouraged system wide, is a pain. You have to be careful here. There is no handy pop-up that says updates are ready, like in Ubuntu. You basically have to upgrade each app on its own or do a security update search. Most just wait for the next iso disk upgrade according to posts on their forum. 

Still, a very slick system.  Also, I have encountered in the past errors with some apps under Sabayon's Gnome, so try this out also. I have not tried the new 3.26 so maybe some of this has been corrected.  I too dislike KDE.

---

### Post by raul_ on 2007-01-13
Actually, after i wrote this post, i did some research and found some benchmark tests that show that the 32bit Edgy is faster than 64bit Edgy. Here's the link

[http://www.phoronix.com/scan.php?page=article&item=616&num=1]("http://www.phoronix.com/scan.php?page=article&item=616&num=1")

---

### Post by mips on 2007-01-13
Gentoo/Sabayon has proper multi-arch support unlike debian based distros.

Getting 64bit up in running in sabayon is a real breeze compare to kubuntu 64bit on which I gave up.

I have not used the 32bit version of sabayon, very happy with the 64bit one.

---

### Post by raul_ on 2007-01-13
> **mips said:**
> Gentoo/Sabayon has proper multi-arch support unlike debian based distros.

Getting 64bit up in running in sabayon is a real breeze compare to kubuntu 64bit on which I gave up.

I have not used the 32bit version of sabayon, very happy with the 64bit one.

since you use Sabayon, can u tell me how good is Emerge compared to apt-get?

---

### Post by mips on 2007-01-13
> **raul_ said:**
> since you use Sabayon, can u tell me how good is Emerge compared to apt-get?

Being a source based distro it takes longer than apt-get. When I say longer it depends very much on the package and installed libs etc. It's not that slow though. For big packages like say Gnome you would just leave it running in the background.

emerge is easy to use and very reliable, when new to emerge it takes a bit of time getting use to it but once you learned the basics it's plain sailing. I'm not into anal optimisation flags etc so just do a standard **emerge -atv *application***.

a=ask/prompt
v=verbose
t=time the process

I'm very happy with sabayon and have not had kubuntu on my pc for about 2months now. I will test feisty when it comes out but i'm bowled over by sabayon.

---

### Post by raul_ on 2007-01-13
I've heard that Emerge kinda "throws away" the advantage of "if it moves, compile it" philosophy of Gentoo. I'm still kinda reluctant though.

---

### Post by Rodneyck on 2007-01-13
> **mips said:**
> For big packages like say Gnome you would just leave it running in the background.

raul, just to be clear, that is (depending on your system) two to three days of running in the background. Compare that to debian's 5 to 10 minutes. This is the extreme, as it is a whole system with many dependencies you are installing, but it is a good example that illustrates that emerge is slower.

---

### Post by mips on 2007-01-13
> **raul_ said:**
> I've heard that Emerge kinda "throws away" the advantage of "if it moves, compile it" philosophy of Gentoo. I'm still kinda reluctant though.

I do not quite follow the above. Using emerge still compiles applications.

I cannot change your mind, only you can. My suggestion to you would be to try the LiveDVD and see what you think.

Faster cpus mean faster compile times. It's only the really big packages that take long. I think my longest compile so far was 1hr30min. Just left it in the background.

---

### Post by RAV TUX on 2007-01-14
> **Rodneyck said:**
> raul, just to be clear, that is (depending on your system) two to three days of running in the background. Compare that to debian's 5 to 10 minutes. This is the extreme, as it is a whole system with many dependencies you are installing, but it is a good example that illustrates that emerge is slower.
not sure what your talking about here?....it usually takes 5 to 10 minutes for me on Sabayon.....

To answer the original post....I have a 64bit computer but use the 32bit version of Sabayon Linux 3.26 (as clearly stated below my avatar)...

To direct you in the path of the most stable Linux OS for a 64bit computer I can only recommend the OS I was using immediately before I switched to Sabayon Linux:[**rPath Linux.**]("http://www.rpath.com/corp/products-rpath-linux.html")

If you want the most bleeding Edge, reliable, fastest OS in existence use Sabayon either 32bit or 64bit version...I suggest you try them both.

If you don't want Beryl or the effiency of a Gentoo OS then I recommend [**rPath Linux**.]("http://www.rpath.com/corp/products-rpath-linux.html")

---

### Post by RAV TUX on 2007-01-14
*moving to the Gentoo forum*

---

