---
title: "Dual Boot: Shrink Volume Questions"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by evankeo on 2009-09-01
Hello all, my name is Evan. I've been booting Ubuntu 9.04 up from a disc for a while now, and love it. I'm finally ready to end my laziness and create a dual boot. I'm using an acer laptop that has about 149 gigs. I was under the impression that I should be able to reduce my main partition by 50% or so, which would leave me with about 75 each for Ubuntu and Vista. But, the shrink tool dialogue box says that the size of my available shrink space is only 41975 mb even though the total size before shrink is 142. If I enter a number any higher, say 41976, the size remaining goes from ~100k to zero. If I'm understanding this correctly, my system is refusing to leave the main partition with anything less than ~100,000 MB. 

Shouldn't I be able to shrink it more if the total size before shrink is 142? I'd like to give Ubuntu more than just 42 gigs of the total size. So, my questions: Anybody know what might be the reason I can't? Secondly, just out of interest, can you change the amounts allotted to each partition after setting up a dual boot? For example, if I allotted less than what I'm allowed to for the new partition, would I be able to go back later and give the new partition more provided the space is still free? I ask, because I'm thinking of going ahead and doing the partition right now, but if there is indeed a way I can free up more volume to shrink, I'd hope that doing the partition now would not prevent me from giving more space to Ubuntu later. Sorry for the excess verbiage and happy to be part of the Ubuntu community. I've been planning on installing linux for ages and it's exciting to be finally using it, even just from boot from disc.

---

### Post by evankeo on 2009-09-01
Okay, so I read about some of the limitations of Vista Shrink tool (e.g. bad clusters of files, the inability to remove around unallocated space, ability only to expand or shrink NTFS or RAW unformatted space, and the unmovable file problems) and the commercial and shareware partition management options and other things one can do/use to get around some of the limitations.  I think I'm on the right track. Apart from standard advice like Defrag, can anyone suggest other topics I should research about what might also be contributing to my inability to shrink the volume I want or what I can do to change this? 

I also know now that I can (in theory) expand partitions at any time.  So, I'm going to go ahead and see if I can get the dual boot done now and just give Ubuntu the ~40gigs the system is letting me give it and then dive into some of these other problems later.  Hopefully, I can get at least this limited partition done without problems - I'll let you know.   Any other ideas about the limitations of the shrink tool, ways to get around them (e.g. recommendations for shareware disk partition management tools etc) so that I can eventually give more space to Ubuntu than what I'm about to allocate would be appreciated.  Thanks.

---

### Post by Mark Phelps on 2009-09-02
Don't know where you read about the Disk Management tool limitations, but the following link provides some advice on how to work around some of them:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

Also, be sure to use the Disk Management tool, even though it does have some limitations.  If you use GParted and force it to shrink, you run the risk of corrupting the Vista OS partition and rendering it unbootable.

---

### Post by Bartender on 2009-09-02
Nice link, Mark.  Saving that one.  

I see one problem with the "fix" that's described if Vista fails to boot.  You need a genuine Vista install disc.  Most people don't get one of those with their PC's, do they?

---

### Post by Mark Phelps on 2009-09-02
> **Bartender said:**
> I see one problem with the "fix" that's described if Vista fails to boot.  You need a genuine Vista install disc.  Most people don't get one of those with their PC's, do they?

I'm presuming you're saying this as a joke, right?

Actually, one of the most serious problems facing folks with Vista is that, after spending $1000 or more for a new Windows box, their tight-fisted OEM won't even provide 15-cents worth of plastic so they can boot into it to repair booting problems.

MOST of the time, all folks get is a "recovery" disk, and all that does is boot into Windows PE such that the only option the consumer has is to completely wipe their hard drive and reinstall Vista from scratch.

... Which is why I'm so adamant about warning people of the risks of damaging their Vista OSs.  If nearly all of them had Vista DVDs such that it was a 15-minute exercise to get their Vista boot back, I'd have no concerns.

Fortunately, MS has "seen the light" on this, and with Windows 7, provides a way to create your own Vista Boot CD to use to repair boot problems.

However, care to guess how many Windows users will bother to notice that even exists, let along take advantage of it?

I don't think I'd be far off if I guessed less than 10%.

---

### Post by ronparent on 2009-09-02
+1 for Mark Phelps comments

Not to get off topic, but, my only Vista machine is my laptop which I avoid tampering with to the extent of using only Ubuntu installed to a usb on it. The effort to restore a fowled up vista exceeds my aceptable pain threshole. My general observation is that the vast majority of windows users do not want to understand or try to tune their systems unless a handy dandy fool proof systems tool is avaiable for any specific purpose. The net results is that if in trouble knowledgeble help is hard to come by. With that said, I admit that these comments are being written in win 7 largely because my Ubuntu Firefox is not displaying the Ubuntu support site properly (no buttons).

---

### Post by Herman on 2009-09-02
> If you use GParted and force it to shrink, you run the risk of corrupting the Vista OS partition and rendering it unbootable.We have already discussed this in another thread.

That How-to Geek '                                                     **[Using GParted to Resize Your Windows Vista Partition]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/")** ' link tells people the WRONG way to resize Vista or Windows 7 partitions, then how to fix the damage it causes.

It would be better to tell people the proper way to do things in the first place rather than waste everyone's time.

It's simple to do it properly.
[IMG]http://members.iinet.net.au/%7Eherman546/p22/012.png[/IMG]
All people need to do is remove the tick from the 'Round to cylinders' checkbox in GParted.
I have written to the how-to-geek asking for that page to be updated, but so far no response.

GParted can usually resize Windows but sometimes it doesn't. When that happens I always run CHKDSK /R and then try again and that usually fixes it. 
GParted resizes NTFS just as well regardless of the state of fragmenation, at least it always has done so for me. 
According to the Parted Users Manual, you don't need to, [2.4.13 resize]("http://www.gnu.org/software/parted/manual/html_chapter/parted_2.html#SEC25") - Parted Manual
The ntfsresize documentation says defragging doesn't matter, [How to resize NTFS without data loss?]("http://darkstar.ucd.ie/timosh/links/ntfsresize.html#example").
According to the Linux manual page for ntfsresize it's not necessary, 
> The  ntfsresize program safely resizes Windows XP, Windows Server 2003, Windows 2000, Windows NT4 and Longhorn NTFS filesystems without data loss. 
All NTFS versions are supported, used by 32-bit and 64-bit Windows.  
Defragmentation is NOT required prior to resizing because the program can relocate any data if needed, without risking data integrity.

---

### Post by Mark Phelps on 2009-09-03
Herman:

I just saw yet another post TODAY about how someone tried to do a side-by-side install using the Ubuntu disk -- and ended up with an unbootable Vista OS.  Fortunately, THEY had a Vista DVD and can repair their OS to make it bootable again.

So, until I stop seeing these posts about Vista being rendered unbootable, I am going to continue to warn people about the risks of using Linux utilities to resize their Vista partitions.

End of discussion.

---

### Post by Bartender on 2009-09-05
> **Mark Phelps said:**
> I'm presuming you're saying this as a joke, right?

Hi, Mark -
No, I wasn't kidding.  I don't know anyone who's gotten a genuine Windows disc along with their new PC in years, but wasn't absolutely sure that it never happens.

Herman, how's it going, that "Round to Cylinders" box is news to me.  Will have to keep that in mind.

---

