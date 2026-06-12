---
title: "Recommendations Needed for a Ubuntu Desktop"
date: 2008-01-08
forum: Hardware &amp; Laptops
---

### Post by slowtrain on 2008-01-08
Hi folks:  I'm looking for a computer to use for some serious number crunching (statistical and natural language processing) and I want the machine to be using Ubuntu.  Does anyone have any recommendations?

I'll want a 64-bit dual or quad core processor.  I've done well in the past w/ a HP Pavilion AMD 64 X2 (4200+) computer, but that's pretty dated by now.  One other concern w/ HP is that it looks like you have to pay for that awful Microsoft operating system.  Can't seem to find much online by way of machines that come preinstalled w/ Ubuntu (Dell has a couple, but they don't seem very powerful).  Maybe if there's a manufacturer that sells w/o an operating system?

Another concern is whether Ubuntu would be compatible with the latest hardware, such as the AMD Phenom 9600 quad-core processor or the Intel Core 2 Quad processor Q6700.  Has anyone tried Ubuntu on machines configured like this?  How about the xeon procesor?

Any input would be welcome!

Cheers, Slowtrain

---

### Post by davarino on 2008-01-09
I am mildly concerned about your choice of Ubuntu for "serious number crunching" on a souped-up machine.

(I can hear the catcalls in the background, but I'll continue.)

If you have looked at all your options, then OK. But I believe that there is a lot to be said for the proprietary OSs and proprietary programs if you're doing intensive stuff - Unix-style methods can be rather kludgey. Serious number crunching is the area where the proprietary OSs do pretty well: after all, academia and business will pay really well for serious usefulness.

Just my two-cents worth.

---

### Post by slowtrain on 2008-01-09
Hi Davarino:  Depends on what you mean by 'serious'.  I'm not a business or govt. agency, just an academic who wants to run some statistical tasks that are computationally intensive.  Colleagues of mine who do serious work in natural language processing use RedHat Linux Enterprise Edition, which I gather is the same configuration as the free CentOS.  I'm used to Ubuntu and think it'll save me considerable time on setup, and I have a somewhat limited grant budget.  Then again, maybe I should be thinking beyond Ubuntu.

What OS's are you thinking of?  How much efficiency gain would you guess there would be?

Cheers, Slowtrain

---

### Post by slowtrain on 2008-01-09
Incidentally, what I need most is an operating system that can run the statistical program R, Java, and a database (maybe Postgresql or Mysql) quickly.  Is there really a big performance difference on such software between free and proprietary unix or linux systems?

---

### Post by hutxubix on 2008-01-09
Though I do not deal with statistics, I work everyday with really heavy numerical computation and we always use Linux. I think is much better unless, of course, you need specific software not available for Linux. (In my case, we program most of it ourselves)

---

### Post by slowtrain on 2008-01-09
Thanks Hutxubix!  It's my impression that Ubuntu is a good deal more efficient than my original Windows OS (kudos for 64-bits and SMP).  The software I use is all open source and available on Linux.  I'd be surprised if propriatery OSs would be a huge improvement in terms of speed.  I've heard I could get a 10-15% performance improvement from Gentoo, but Gentoo was just too unstable to be worth that kind of performance gain (rebuild somehow wrecked my C-path and lots of other problems).

Peter

---

### Post by slowtrain on 2008-01-09
Incidentally, my question remains:  What higher-powered systems have people tried Ubuntu on and how successful was that?  Any suggestions on where I can get a computer that does not require the purchase of Windows?

---

### Post by davarino on 2008-01-10
My step-son built us a really nice compu (686 32-bit 512M Ram 250G HD) for about $600 in parts (inc. WinXP) from Tiger Direct two years ago. It was pretty much plug and assemble as I remember it... less than 2 hours for sure. (If you build from parts you *certainly* don't need to purchase Windows to go along with them.)

I'm sure you could do much better today than that, and if you know somebody a little handy with building computers you could have a roaring system for not a lot of money at all. (Maybe all you'd have to pay is a good home cooked dinner.) :)

About proprietary OSs: if the programs you listed are all you want to work with, you'll do fine with Ubuntu. If you're into lots of **heavy** analysis, then WinXP is worth looking at for specifically optimized software. Most people (even us math geeks) are not into heavy analysis (at least not on a regular basis). Remember, though... go for the programs that do what you want, the choice of OS is really secondary. (That last remark is heresy to some... it's gospel to me.):p

Good luck.

---

### Post by manimal347 on 2008-01-10
Agreed. Any computer bought from a retail store isn't exactly ideal for running statistical equations. Go to Newegg and build a system around a new Core 2 Duo chip. Those things overclock insanely... and run stable while doing so even on the stock cooler. I don't own one, but that's what most gamers, who as we know push their CPU's to the the edge in games like Crysis, have been saying. Many of the storebought Core 2 Duo systems can't be overclocked, perhaps costing you up to 30% of your potential MIPS/FLOPS! AMD shouldn't even be a consideration unless you have utmost loyalty, as even the new Phenom's are trounced by a sanely-overclocked budget Intel. This pains me, as I've bought AMD since my first machine, a heavily used 386-DX40, but it's true. Overclocking still eeks many people out, but I can''t see your research as being NASA launch-critical if you're running it on an HP and considering a Dell, both companies that load up on generic Taiwanese parts (EX: Hynix over Micron/Crucial, Bestec over Seasonic) and use 300 watt (if lucky) power supplies. Plus, the Intel chips are considered grossly engineered, while the AMD chips, scarcely changed from your "old" 4200x2, run ragged and have very little margin for overscocking (or marginal cooling).

If you're not comfortable building your own system, perhaps you know someone who can do so for a moderate fee? This way you can ensure your system only uses high-quality components that are known to work well under Linux and will survive the rigors of crunching numbers for days on end. If not, your local whitebox vendor (few left...) may be able to build you a custom ystem of the highest quality parts, though nowadays you'll pay a hearty markup and had better do research on both the firm's reputation and check over the various part brands they'll use.

Also, Ubuntu is scarcely the scientific distro of choice. You need performance and minimal cruft over everything else, I'd presume, so maybe a base-install of Debian Etch is your best bet? I personally like that distro, and if you're familiar with the CLI methods of using Ubuntu, you'll be right at home. A base-server install of Ubuntu also works and is more up to date than Etch, but from personal experience, there's few people to turn to for help and little official recognition that end users even do this in the Ubuntu Wiki. Most pages and forum posts assumes you've got the standard desktop install of Ubuntu or Kubuntu, not a system running Fluxbox or Blackbox and lacking things like Synaptic, Cups, Ubuntu-designed configuration GUI's, or stock apps like Gaim and OpenOffice. In the Debian world, people don't assume everyone is "green" by default and expect that some people do things like compile many of their own apps, prefer CLI, or actually know how to use Vi and Emacs (or at least nano/pico).

An assortment of vendors do sell Linux systems, including Ubuntu ones, but they usually cost more than a nice Windows Vista-licensed machine from a reputable (Read: non e-peen/without 600$ automotive finish) gaming-rig company like Velocity Micro or ABS, and offer much less in features, part quality, and expandability. Some of these Linux machines are HP or E-machine quality yet break a thousand dollars for a rather basic computer, thus suggesting the "Microsoft tax" false canard once economies of production and app-bundling payments from companies like RealMedia are factored in. Indeed, even Dell only gives about 10$ off its Ubuntu and Freedos machines- if lucky. You can always delete your NTFS partition later... or sooner, so what OS it comes with shouldn't be a deciding factor.

As for what Davarinoi said, buying yourself a Sparcstation would just be silly these days for what you need. Linux IS enterprise class, and indeed, displacing real unixes. Note that 85% of the top 500 computers in the world run Linux, and only 6% run  a proprietary Unix, many of them older machines edging towards retirement. It's no accident even proprietary OS vendors like IBM and SUN are publicly embracing Linux. I'd quite like to see a closed-source OS that scales to about 850,000 CPU's, as IBM's newest Bluegene computer can.

---

### Post by manimal347 on 2008-01-10
Oh, you also asked what CPU's the Linux kernel supported. A modern version, such as shipped with  
Ubuntu Gutsy should support practically any I486+ chip fine, even a quad core Penyrn. A few optimizations might conceivably not be in the ubuntu kernel, but you can always compile your own or get a colleague to help you with that. In any case, as Intel and AMD chips are backwards compatible, 
newer models will work fine and give significant performance boosts.

I'd worry more about hardware like graphics boards, things that doesn't concern raw IO throughput and data crunching, though as new bus and drive connection standards come along, Linux can be sluggish to support them, especially in mainline kernels.

And yes, Gentoo can be rather buggy and only offers a very modest performance boost considering the hassle. People consider it an enthusiast OS and compare it to an American muscle car you tinker with on weekends, though some servers do certainly run on Gentoo, and it CAN be a viable production environment.

---

### Post by slowtrain on 2008-01-10
Hi Manimal:  Thanks for offering such detailed and immensely helpful information.  I've done some double-checking and, yes, the core 2 duo outstrips the AMD processors these days.  In particular, I'm now lusting after the Intel Core 2 Quad Q6600 2.4Ghz.  Could have four processors running separate tasks, and the chip barely costs $250!

Thanks also for the tips on Windows generally not adding much to computer prices and Tiger Direct and such.  The game console makers like Velocity must be using some very high quality parts--they're charging $2100 for a Q6600 based system, while I can get a system build around Q6600t elsewhere for maybe $1000  I wonder if the quality difference is worth it (would it help number crunching performance?), esp. if I'm not likely to use the computer for more than a couple years.

My problem w/ Tiger Direct is I'm not a hardware hobbyist or computer engineer and regrettably know no one who is.  Tiger Direct has some great game cases w/ much of the hardware I want, but I don't have time to put the parts together and don't trust myself to put in the right cooling components (potentially some bad mamba).  You don't seem too keen on the quality of HP components, but one nice thing about their website is that it guides you through putting together a system and then builds it for you.

Does anyone know of a higher-quality computer maker that also provides good guidance on putting together a system and then builds it?  Or perhaps a service that works with a customer to put something together?

Right now my main options seem to be to go back to HP or maybe talk w/ a company like Zareason, which builds inexpensive Intel / Ubuntu systems.

Cheers, Slowtrain

---

### Post by gletob on 2008-01-10
its states in the EULA's of any Microsoft OS the if the buyer of an OEM machine refuses to accept the EULA the OEM must provide a refund
EDIT : by the way [System76]("http://system76.com/")

---

### Post by slowtrain on 2008-01-11
Thanks Gletob!  Money back via the EULA--they don't exactly advertise that! 

I just found a system at Zareason that apparently nicely meets my needs, for barely $1k, and is built around Ubuntu.  

Has anyone had any experience w/ ZaReason?  I can't seem to find the company on the BBB website.  There does seem to be a bit of buzz about them in Ubuntu circles, but I'm wondering how reliable they are and how high quality their hardware is.

Cheers,

Slowtrain

---

### Post by stuartmacgregor on 2008-01-22
Slowtrain, i am in a similar situation to you. I work in academia and want a fast machine for doing statistics and handling very large biological data files. I've just ordered a top end Dell machine with a quad core processor etc (Precision T7400n). It apparently can run RH enterprise linux ( [https://hardware.redhat.com/show.cgi?id=423751](https://hardware.redhat.com/show.cgi?id=423751)
 see dell link there too ) although I'd like to run ubuntu on it if possible as my understanding is that RHEL just offers more hand holding for the support and no actual performance benefit (but I'd like to know if anyone has evidence to the contrary). I'll get back to you on how I get on with ubuntu if you are interested. 


To answer at least part of your question, yes Dell do offer ubuntu on some low spec machines - they also offer RH enterprise linux and suse based linux (novell) on a wide variety of machines although of course the cost of these (i.e. cost of commercial support) is similar to windows. In some cases they do offer "no OS" although this tends to be just the "server" models and in my case I was interested in a "desktop" model. The options also vary depending on where you are - I'm in australia and the options that dell have here are much less flexible than in say the US.

Stuart
[email]stu.macgregor@gmail.com[/email]

---

