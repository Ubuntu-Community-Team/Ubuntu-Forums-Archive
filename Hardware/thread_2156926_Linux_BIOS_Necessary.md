---
title: "Linux BIOS Necessary?"
date: 2013-06-23
forum: Hardware
---

### Post by incurablegeek on 2013-06-23
I plan to use an ASRock 970DE3/U3S3 motherboard in my Ubuntu Linux build. Now I have often been accused of over-thinking things, but I do prefer accuracy over slap-happy.

On my last Linux build I used an Asus board which did have a*** "for other" BIOS ***which I assumed to be specific to Linux - since it wasn't for Windows.

Here's the BIOS download page for the ASRock which has only Windows stuff listed [http://www.asrock.com/mb/overview.asp?cat=Download&os=BIOS&Model=970DE3/U3S3](http://www.asrock.com/mb/overview.asp?cat=Download&os=BIOS&Model=970DE3/U3S3)

**Is Linux fussy about which BIOS version you use?**

---

### Post by sanderj on 2013-06-23
"for other" could mean you can install that BIOS *NOT* using Windows.

However: why update the BIOS? Just try Ubuntu and see if it works. If it ain't broke, don't fix it.

---

### Post by incurablegeek on 2013-06-23
> why update the BIOS?

Why update? First of all, most serious computer users try to keep their BIOS up to date.

As to > "for other" could mean you can install that BIOS *NOT* using Windows.

No sir, these are all *proper* BIOS updates, i.e. **flashing the BIOS** with USB thumb drive. I never update a BIOS within the OS.

As for > Just try Ubuntu and see if it works.  I think that makes sense. Why do otherwise since the only options provided by ASRock are Windows or DOS. I'll simply flash the BIOS with the latest version (which btw almost never ships with a new motherboard - and be done with it.

Thanks.  :)

---

### Post by Mark Phelps on 2013-06-24
First of all, any "serious computer user" should already know that a BIOS is completely independent of an OS.  There is no such thing as a "Linux BIOS".

Second, keeping the BIOS up to date is NOT along the same lines as keeping drivers current and/or keeping app versions current.  BIOS updates are made to (1) correct errors and/or (2) add capability for new hardware.  If neither of these applies in a particular case, there is no reason to update the BIOS.

And finally, it's possible to trash a PC by upgrading a BIOS simply to stay "current" -- I know because I had it happen on a recent Gigabyte motherboard.  Fortunately, for me, since I always save off the current BIOS in a way that makes it restorable, I was able to restore the working BIOS version.

So no, I do not advise updating the BIOS version simply to stay current.

---

### Post by incurablegeek on 2013-06-24
> So no, I do not advise updating the BIOS version simply to stay current.

I'm new to Ubuntu. I'm definitely not new to computers. I've been keeping my BIOS current for 25 years. The BIOS that came with the motherboard is 1.0. The current BIOS is 1.7

If you read the attachment from ASRock, you will see that there are many good reasons to upgrade the BIOS.  And, yes, I do know full well what the BIOS does. I also make manual adjustments to the Win Registry routinely. 
No need for fear if you know what you are doing.  :)

Besides, as I'm sure you know, even if you do corrupt the BIOS, So What!  You just buy another CMOS and tell the mfr. what BIOS version to load - or you do it yourself. About a $20.00 mistake - to learn something. Not a bad deal.

Trust me. I have yet to meet anyone who knows hardware better than I. I've built many hundreds of computers and flashed too many BIOS to count.

As for Linux, Windows 8, Windows Server 2012, the new Win File System that will replace NTFS, ReFS, programming languages for Website Design? No, I don't know them well yet. That's why I am presently studying them.
I've been studying and learning all my life.

Thanks for your help. I will update the BIOS by flashing it as always. And then assume that sanderj is correct. It worked before on the "other BIOS" (whatever the heck other means), so I should be OK.

Thanks so much.

I have a practice on the net of not saying too much about myself or what I have done in my life. Being new here, I am necessarily reticent to disprove any of the spurious comments made to my post, e.g. "the BIOS has nothing to do with OS and software". That statement has its own built-in self-refutation.

OR "Flash the BIOS and die".   Also, well beyond silly.  

OR "no need to ever update the BIOS"  Absolutely hilarious, in a rather sad way.

The only time I ever had a bad or corrupt BIOS was on a new motherboard which came with an outdated BIOS version. Just FYI the BIOS on a new motherboard is almost always old, if not elderly. Well, this CMOS was unusual in that it would not hold a BIOS update. Why? Because the CMOS itself was defective. Well, instead of RMA'ing the entire board, I bought another CMOS. It's very easy to replace, if you know how. :razz:

Oh, and yes, I do know just a bit about IC's. I used to export them to China way back when. If you ship an order and don't get the specs right, you eat the shipment and lose a bunch of money. No fun at all.

That's as much as I care to reveal about myself. 

Thank You!=D>

---

### Post by VMC on 2013-06-25
What the "other BIOS" may mean is legacy BIOS, as opposed to GPT or EFI. The problem now is windows 8 secure booting. 
Are you going to be booting only Ubuntu or a combination thereof? Let's go from there.

By the way, there was going to be a Linux BIOS of sorts, called [core boot]("http://www.coreboot.org/Welcome_to_coreboot").

---

### Post by CharlesA on 2013-06-25
> **Mark Phelps said:**
> So no, I do not advise updating the BIOS version simply to stay current.

I stand by this.

All of the newer mobos I have used have supported flashing the BIOS from within the BIOS or before booting the OS. [ASRock has the same thing.]("http://www.asrock.com/support/BIOSUI.asp?cat=BIOS")

It is listed under "Instant Flash" on the BIOS download page.

Take note of the warning on the bios download page:

> We don’t recommend users to update the BIOS if their system is already running normally. ASRock® assumes no responsibility for any damages caused by improper operations of downloading or updating the BIOS. Before you download or update the BIOS, please read " (How to Update)" below carefully.

As far as your original question goes, I don't think Linux really cares. You might need a newer kernel if you have new hardware , but in general it shouldn't care. Now if you have to deal with Secure Boot, like  VMC said, you might run into issues with dual booting Win8 and a flavor of Linux.

Anyway, if you really want to update the BIOS because the version on the board is a year old, go for it but make sure you make a backup of the current BIOS if the software supports it.

---

### Post by incurablegeek on 2013-06-25
I do wish to thank to thank Oldos2er for the kind PM he sent me.

Quite frankly, I should never have used the expression "as every experienced computer user knows". While quite true, it did seem to denigrate the computer knowledge of others in the forum. Such was not my intention. On forums, in emails, and other forms of e-communication, I am super careful about choosing my words carefully. However, all my life I have been in a position where my truthful opinion was valued more over what the Chinese call "***pai ma pi***". It literally means to "pet the horse's ass" and is a metaphor for ***shaping*** the truth so as to make it more diplomatic or flattering. I've never been good at that.

Two things:

1) > We don’t recommend users to update the BIOS if their system is already  running normally. ASRock® assumes no responsibility for any damages  caused by improper operations of downloading or updating the BIOS.  Before you download or update the BIOS, please read " (How to Update)"  below carefully.

That's a boiler-plate legal disclaimer to protect the manufacturer from a frivolous lawsuit brought by someone who tries to flash a BIOS, doesn't know what he is doing and then tries to blame his failure on ASRock. That's why I used the (now seemingly inappropriate) expression "as every experienced computer user knows". For the record, I did not post my question about whether or not Ubuntu had special requirements in CMOS software to receive a lecture on the BIOS.

Just to help those of you who are terrified of the BIOS. The BIOS is not a chip. It is actually a program written to a CMOS, an IC that looks kind of like a cockroach. And a CMOS is in turn an EEPROM, with ROM meaning Read Only Memory. (The chip cannot be modified.) A PROM is a programmable read-only memory chip. (Data can be written only once.) An EPROM is an erasable programmable read only memory chip. (This PROM can be written to again, but requires special equipment to do so.) An EEPROM can be written to (flashed or reprogrammed) anywhere from 10's of times to many thousands of times.

So the BIOS once again is the software written to, or erased and then written to again, on the CMOS chip which is technically called an EEPROM

Why keep it updated? The quick and easy answer is to keep your computer running at peak efficiency. Now my ASRock board is the cheapest board I own, but it's rather new. Because of its newness, it can handle 8-core AMD CPU's. As I said before, though, the BIOS on a newly purchased motherboard is always OLD. Mine is BIOS #1.0 The current BIOS is 1.7 I have experienced in the past that other boards that could handle 6-core AMD's could only do so after the user upgraded the BIOS. Otherwise the poor motherboard with the legacy BIOS would see your brand-new 6-core as a 4-core. If I seem a bit inappropriate here, please excuse me. But motherboard manufacturers offer BIOS upgrades _**for a reason**_, and not because they have too much time on their hands. 

As to the statement of "if it ain't broke, don't fix it", I can only say that flies in the face of the Hegelian dialectic which I have followed all my life. Basically and at the risk of oversimplifying Hegel, one must endeavor to halve 1 ***ad infinitum*** to become 0, with Zero representing perfection, i.e. God. Scientists have been doing it for many years now. Well, I have developed lots of educational programs and curricula over the years. And at the end of the year I always tore up what I had designed and that everyone was pleased with - and threw it in the trashcan. I then spent the next 6-8 months rewriting the entire program, many hundreds of pages until I had achieved what I believed was, with years of testing, to be the maximum efficiency possible. That process consumed 15 years and over 20,000 hours of computer work.

The same with my computers. They are near and dear to me. I have 3 computers and a file server, all of which have about 40 TB of storage. Since I have approximately $20K invested in this setup, I show them respect. I keep them up to date and running as efficiently as possible.

As to my question about whether or not Linux required a specific BIOS or BIOS configuration, that confusion if you will arose from a new development by Microsoft. As far as hardware, there haven't been any really improvements in about 5 years, not from Intel, AMD, motherboard manufacturers, etc. But the replacement of NTFS with ReFS (Resilient File System) is quite a big deal.  [URL="https://blogs.msdn.com/b/b8/archive/2012/01/16/building-the-next-generation-file-system-for-windows-refs.aspx?Redirected=true"]https://blogs.msdn.com/b/b8/archive/2012/01/16/building-the-next-generation-file-system-for-windows-
refs.aspx?Redirected=true[/URL]

As for my Loony Tunes question about a specific BIOS for Linux, I simply wanted to know if AHCI (Advanced Host Controller Interface) or a specific Linux AHCI was the drug of choice. Simply Google the question and you will surely find discussion on this very question [http://www.ocztechnologyforum.com/forum/showthread.php?69299-BIOS-modes-IDE-vs-AHCI-vs-Linux-AHCI-!-!](http://www.ocztechnologyforum.com/forum/showthread.php?69299-BIOS-modes-IDE-vs-AHCI-vs-Linux-AHCI-!-!)  It doesn't take long to figure out that most of the forum Gurus are having trouble with the difference between IDE, AHCI, SCSI, or Linux AHCI.

Sure, on the surface, my question appears either idiotic or at least unduly pedantic.

What I had hoped when I posted this question was to stimulate an intelligent discussion on the issue. I failed greatly, though I was quite sincere.

As I told the Admin who so kindly PM'd me, I love the internet, forums, emails, and all the forms of e-correspondence available. I also fear them greatly, because it is so easy to offend either with my blunt honesty or my sense of humor. All my life, I have been paid for my blunt-force honesty. Never will I buy into the Politically Correct movement, because of reminds me of censorship or a kind of relapse into the Dark Ages of history.

With that said, I do sincerely apologize if I stepped on anyone's toes. I shall be more careful in the future. :)

---

### Post by Mark Phelps on 2013-06-26
We get a LOT of folks coming here who think, "my pc is not performing as well as I would like, I know -- I'll just update the BIOS and everything will be better!" -- without any knowledge of the downsides of doing that.

Since you appear to have great expertise in this area -- then go ahead, try it.  When you really do know what you're doing, there is little or no risk in doing that.

I do know something about BIOS's, as years ago, I wrote firmware myself.  It was not my intent to insult your intelligence; I was only trying to provide a caution.  If that came across as insulting, you have my apology for that.

---

### Post by incurablegeek on 2013-06-26
Mark,

Everything is totally cool. What I was trying to do in my last post was 1) provide some information about the BIOS so as to demystify it -and- to basically apologize for coming across too strongly in my initial post. So again, my sincerest apologies.

> my pc is not performing as well as I would like, I know -- I'll just update the BIOS and everything will be better!
Your are totally and absolutely right about that! What I was trying to say is that there are many reasons to keep your BIOS up to date so as to keep your computer running at max efficiency - BUT updating the BIOS is the last thing you need to check to "fix your computer". Adjusting the settings in the BIOS, yes. But not flashing the BIOS to fix a computer, NO.

There is just no single "cure-all" for fixing a slow computer or making it run faster. If we are speaking to the "newer" computer users, you need a good firewall and an Antivirus first, before you install programs. The free stuff is just as good as the "pay through the nose" stuff IMHO. I use Comodo firewall and Avast AV. For routine cleaning, I use Spybot, Malwarebytes primarily - also PrivaZer, rKill, KeyScrambler and for passwords I use KruptosRandom (free password generator) and LastPass for keeping track of my passwords. Also, I highly recommend cCleaner for cleaning up your browser (I use Firefox because I like the addons, but none of the browsers are secure.) and your Registry. Please beware of other Registry Cleaners! Raxco Perfect Disk is super good for optimizing your SSD and defragmenting your hard drives. My apologies if some of this stuff doesn't have Linux correlates or is unnecessary for Linux.

Final comment: All my life I have considered myself to be a work in progress. Quite frankly, my knowledge of computers is like Swiss Cheese - There are some things I really know a lot about, and there are some things I know very little or nothing about. Ask me in 500 years and I will probably say the same thing.

Interesting article: ["I Contribute to the Windows Kernel. We Are Slower Than Other Operating Systems. Here Is Why."]("http://blog.zorinaq.com/?e=74")  [http://blog.zorinaq.com/?e=74](http://blog.zorinaq.com/?e=74)

You guys are first class!  Thank you for having me in your forum!

---

