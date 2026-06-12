---
title: "Linux Adverse Effects Upon Laptop Hard Drive Reliability - Are Facts Available"
date: 2007-08-16
forum: Hardware &amp; Laptops
---

### Post by porcorosso on 2007-08-16
I've seen a few posts here and there containing rather worrisome implications about the Linux kernel(s) used in Feisty Fawn (and other distributions, of course) and the potential they have for causing premature failure on some types of laptop hard drives.

Does anyone have any factual data on this issue, or are the messages about this merely conjecture? I'm currently dual booting my somewhat expensive Dell Precision M70 notebook computer between Vista and Feisty Fawn (installed via Wubi). I have noticed a strange, brief whining sound whenever I shut the system down from within Ubuntu. When I shut down from within Vista this sound is not made by the system.

For the time being I have taken to not shutting the system down from within Ubuntu. When it's time to quit, I just reboot into Vista, and then shut down from the Vista logon screen.

I tried looking for solid information about this matter, but what I've found so far doesn't seem to be confirmed anywhere authoritative.

If this is a real bug, I'd also like to know whether or not it's going to be fixed it the next Ubuntu release.

---

### Post by Sunflower1970 on 2007-08-16
I've read the same posts about Feisty's kernel. 

Just recently, I upgraded the kernel to the 2.6.22-9 kernel and the sound went away on my laptop (oh, and suspend worked again. Woohoo!) using this guide: [http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

---

### Post by porcorosso on 2007-08-16
Thank you. That thread, however, was one of the threads I'd already discovered. I didn't think that it really gave much information about whether or not this shutdown issue actually does constitute a threat to the well-being of laptop drives.

The thing is that upgrading the kernel in this manner is not likely to be without quite a few ramifications. I'd rather stay as "official" as I can with my Ubuntu installation. I'm evaluating it and would rather not be wondering whether any problems I see are due to the distribution itself, or whether they may be due to my having done something wonky TO the distribution. You know what I mean? If this were just a hobby box I'd go for it. But I'm using this system as a remote admin system for a work network, so I'd like to stick as close to standardized Ubuntu installations as possible.

I do appreciate your help, though. Did you see anything in that thread (or elsewhere) that actually gives solid details about this matter? If there's solid information about a bug in that thread I missed it. Which is entirely possible -- because it's a long thread, and I'm a tired old man!

:)

---

### Post by kelvin spratt on 2007-08-16
their is not  and never was a problem 20 years was given as a bench mark, all these fears are just to put fear into people By?.

---

### Post by Sunflower1970 on 2007-08-16
The only other info I've seen on it was this thread: [http://ubuntuforums.org/showthread.php?t=508576](http://ubuntuforums.org/showthread.php?t=508576) which I'm sure you've already read. I think there are a couple of links to some launchpad bugs on the issue, but I've not really seen anything else about it. 

The noise issue does seem to be resolved in Gutsy, though (I no longer have the *klunk* sound when I shut down with the Gutsy kernel--it's nice and quiet)...and luckily it's only about 2 mos away before it comes out. :)

---

### Post by porcorosso on 2007-08-16
> **Sunflower1970 said:**
> The only other info I've seen on it was this thread: [http://ubuntuforums.org/showthread.php?t=508576](http://ubuntuforums.org/showthread.php?t=508576) which I'm sure you've already read. I think there are a couple of links to some launchpad bugs on the issue, but I've not really seen anything else about it. 

The noise issue does seem to be resolved in Gutsy, though (I no longer have the *klunk* sound when I shut down with the Gutsy kernel--it's nice and quiet)...and luckily it's only about 2 mos away before it comes out. :)

Thanks. Yes, I had seen that thread. There's a lot of angst in there! But there just doesn't seem to be a lot of real information.

My installation has never made a "klunk" at shutdown, just a sound that almost sounds as though it could be coming from the sound card instead of from a electromechanical device like the hard drive. But the decreasing pitch of the sound is suggestive of a spin-down sound. It's exactly the same sound it makes if I have to perform a hard shutdown on the notebook by holding the power button in the depressed state for a few seconds. I'm sure it's best not to do that if it can be avoided, and I'd guess that I'm better off not shutting down directly from Ubuntu if I can avoid it, too. The sound is made at no other time -- not from shutdown from Vista, and not when rebooting from either OS.

If this sucker had ever made a klunk when shutting down from Ubuntu, I'd have yanked the OS off of the hard drive. Klunks are not a happy sound in a computer. Well, not since my Apple //e a long time ago. The drives on those things (floppy) made hilarious sounds.

;)

As it is, this is a little worrisome, and I think I'll continue to reboot into Vista before shutting down. It's a little irksome to waste the time, but I'd rather waste a wee bit of time than the hard drive.

In any case, it's a really remarkable distribution (Ubuntu), and I'm enjoying the heck out of learning about it. (Folks around me are complaining bitterly that they can hardly get me to do anything else!)

And I'm looking forward to Gutsy Gibbon.

But the names of these releases -- really! Heh.

---

### Post by buntunub on 2007-08-16
I originally thought that these posts about software screwing up a hard drive was baseless FUD. I looked into it (google is your friend, try it sometime), and found that it is indeed and in fact, baseless FUD.

Please stop posting this type of nonsense.

---

### Post by porcorosso on 2007-08-16
> **buntunub said:**
> I originally thought that these posts about software screwing up a hard drive was baseless FUD. I looked into it (google is your friend, try it sometime), and found that it is indeed and in fact, baseless FUD.

Please stop posting this type of nonsense.

To whom are you addressing your request? It's pretty darned clear that I was doubting the veracity of the claims about hard drive damage. Nonetheless, caution is always advisable -- especially on an admin system that sees a lot of use. And a Google search doesn't necessarily produce more convincing evidence that a search of the Ubuntu forums. If you found specific evidence that absolutely proves your baseless FUD claim, then why not produce the link?

Google is your friend, indeed. 99% of the hits from most Google searches ARE fud.

While we're making suggestions about behavior, maybe you could try using a civil tone?

---

### Post by buntunub on 2007-08-17
I found several sites which discuss this very subject, all of which prove that there is no sound evidence to support this wild and baseless claim. I dont need to prove anything to support or disprove your claim. Its your claim, so the burden of proof is upon you (or anyone who makes such a wild statement as this one is). What is the evidence to support this anyway?.. Yes, I understand that some claims have been made about it, but not a single one with supporting evidence, logs, etc.. Not a one. Its all "linux destroyed my drives!!", or "I heard so and so say that linux screws up hard drives", or "I seen alot of posts about this". Its all FUD plain and simple until proven not to be with hard evidence.

Maybe I misunderstood the tone of your post, or its intent?

---

### Post by porcorosso on 2007-08-17
> **buntunub said:**
> I found several sites which discuss this very subject, all of which prove that there is no sound evidence to support this wild and baseless claim. I dont need to prove anything to support or disprove your claim. Its your claim, so the burden of proof is upon you (or anyone who makes such a wild statement as this one is). What is the evidence to support this anyway?.. Yes, I understand that some claims have been made about it, but not a single one with supporting evidence, logs, etc.. Not a one. Its all "linux destroyed my drives!!", or "I heard so and so say that linux screws up hard drives", or "I seen alot of posts about this". Its all FUD plain and simple until proven not to be with hard evidence.

Maybe I misunderstood the tone of your post, or its intent?

You certainly did misunderstand the tone of my post AND its intent! If you read what I have said -- NOWHERE did I make any claim other than one of the claims you yourself have made in your reply above -- that I had seen many suppositions about this but nothing even approaching a proof. I was ASKING if anyone had ANY REAL INFORMATION about these claims. That's clearly not a matter of me claiming that Linux is damaging anything.

The reason I asked the question is that there is an obvious, observable difference in the behavior of this system (the Precision M70) when it is shut down by this particular Linux distribution (Feisty) than I have seen from Windows XP, Windows Vista, or an older version of Debian briefly installed a couple of weeks ago before I decided to test Ubuntu instead.

I also used to write drivers for Zilog and 6502 systems, and I know for a fact that it is possible -- even easy, as in by accident -- to write driver and firmware code that damages hardware -- particularly electro-mechanical devices like hard drives and heavily taxed specialized processing systems like graphics subsystems.

So I asked if anyone had proof one way or another about this supposed issue with some kernels causing shortened lifespan in hard drives.. And I wasn't particularly thrilled to have my question called "nonsense", or to have you state that I am making any kind of claim as to authenticity of any of these posts about the matter.

I think I made myself pretty clear, and the only bow I made to the possibiltiy that there might be such a problem was a statement about my workaround to prevent having to shut the system down directly from within Feisty. That's just cautious behavior that harms nothing and costs me only a few seconds at shutdown time. I haven't performed any kind of surgery on my installation of Ubuntu, like changing the kernel from the officially supported one -- not that I have anything against people who have done that. Each of us deals with perceived risks in his own manner. I'm pretty conservative.

So, in what way was I spouting nonsense or being an hysteric? I had searched for information on various newsgroups and had hardly found anything at all about the subject -- and certainly no kind of "proof" of anything. I came to the Ubuntu forum, which is supposed to be the best place to find out about this stuff, and asked the question.

The original post asked a question. Does anyone have an answer, as in genuine empirical data -- not anecdotal evidence -- on this issue? Frankly, I doubt that anyone has actually "proved" anything one way or another. That project would require considerable expenditure of effort and time, and a large variety of test machines. But a stipulation by a primary developer, for instance, that the method these kernels use for handling the hard drive at shutdown has been used successfully (as in no reports of adverse hardware effects) and commonly with the same sorts of systems that people have claimed are now being damaged would go a long way toward assuaging any fears that thoughtful end users might have.

On the other hand, if a new trick was tried, or if old methods are being used on new types of hardware / firmware combinations -- well, anecdotal evidence is almost always the starting point for the investigation of phenomena. Sometimes those investigations prove the suppositions to be false. And sometimes they prove them to be true.

I repeat the question. Any solid data out there? Or just suppositions on one side or the other?

---

