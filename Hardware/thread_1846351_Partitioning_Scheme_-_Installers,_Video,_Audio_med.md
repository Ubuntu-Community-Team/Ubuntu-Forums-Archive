---
title: "Partitioning Scheme - Installers, Video, Audio media - diff/same parti"
date: 2011-09-18
forum: Hardware
---

### Post by johntkucz on 2011-09-18
Member




Join Date: May 2011
windows 7 home 32 (and Home Preimium 64 version) as OFF-os, main OS is ubuntu 10-11
41 posts
 
          
Partitioning Scheme - Installers, Video, Audio media - diff/same parti
back at partitioning wahoo! 
it's a bit cryptic. computer HD is my home so I put a lot of thought into these partions. Iloe the math and figuring this out!!


14R_500GB!	shorthand	"+ if not ntfs"	PR only if primary	content	ORIG only if original, otherwise its a BU	important folders in partition	
35	Windows 7	 PR	Windows 7 home pro or ultimate	
105	db	 dropbox	
20	usrd	 userdata	ORIG	
190	apps	 nongame_apps, games	
100	ext_int_insta	 extvm extam intvm installers	
50	down_scrt	 dold/temp scrt (downloads and scratch disk)	ORIG	xfer_to_2TB_intvm xfer_to_1tb_extam xfer_to_1tb_extvm exfer_to_2tb_installers	
20	lin	+'	PR	linux 11.04 ubuntu	
500	





1TB	1TB	
105	db	 dropbox	
320	int_vm	 invtvm	
150	ext_vm	 ext_vm	ORIG	
150	ext_am	 ext_am	ORIG	
150	inst	 installers	
100	down_scrt	 down/temp scrt (downloads and scratch) xferTO_2tb_intvm	ORIG	xfer_to_2TB_intvm xfer_to_1tb_extam xfer_to_1tb_extvm exfer_to_2tb_installers	
25	lin	+'	PR	linux 11.04 ubuntu	
1000	




2TB_int	
70	Windows 7	 windows 7 home pro or ultimate	
30	usrd	 userdata	ORIG	
900	apps	 nongame_apps, games	
105	db	 dropbox	
320	int_vm	 invtvm	ORIG	
150	ext_vm	 ext_vm	
150	ext_am	 ext_am	
150	inst	 installers	ORIG	
100	down_scrt	 down/temp scrt (downloads and scratch)	ORIG	xfer_to_2TB_intvm xfer_to_1tb_extam xfer_to_1tb_extvm exfer_to_2tb_installers	
25	lin	+'	PR	linux 11.04 ubuntu	
2000	



Main concern. I want to dual boot in linux and windows. No prob at all. Iv'e triple booted (with rubbish mac os) on a machine before. The only prob is dropbox syncing and file systems. I know windows can't access ext4 (correct?)

linux seems to access ntfs fine. I guess I'm just wanting more information on....

dual boot with dropbox
and
MAINLY, any problems of accessing read/write to 4-5 ntfs partitions FROM ext4 linux OS boot on a regular basis.



A CONSIDERATION THAT SOMEONE MIGHT PROVIDE INSIGHT ON

external video media (videos that I didn't make) = extvm
external audio media (audio files namely classical music and audio books that I didn't record) 

fyi all the external folders are considerably small in size to the internal oens (i.e. I have more recorded audio and video that I did myself than of external type)

installers_games
installers_games_savedgame_data
installers_apps

ALL 5 of those are IMPORTANT (not as important as the internal stuff) but important

I dislike discs. 
the conundrum or consideration rather is 

extvm on 100gb partiton currently 38.8gb so plenty of space # this makes sense because I would want maximum size of extvm and not too muc
extam on 100gb partition
Cheers!


----------

do I put external video and exteranl audio and installers all on the same partition 
OR
those three on three separate partitions
OR 
external audio and video on same partitions and installers on separate?




--------------

this is all moving towards building my own rig, something that has been a DREAM (I have traveled the world done some amazing things, but being a genuine nerd, building a rig is more of a dream) for many ehars.

It will likely be 
3,830GB of data
but really it's only 1TB of data (abou 600-1000gb) that is just backed up extensively. and then space for application installations!!

---

### Post by johntkucz on 2011-09-18
---------------


all the new words are clusters of data 

extam for example is external audio media (audio media I didn't create).  I have much more recordings done by me, than say, audio books read by someone else so I differentiate between those.  

Thus partitioning makes sense to have set "quotas".  I know windows 7 has a quota system for users but that doesnt' seem specific enough.

I have expeirenced copious small partitions which are a headache.  I think limited the partitions to 4 or so DOES make sense.

I've spreadsheeted and tabulated ways to divvy up the 500GB about every day (multiple times a day) usually right when I wake up for the past two weeks!  Finally got computer now and am freezing haha!!!

After having so many partitions (becaue of a triple-boot on crap mac which I loathe) and other reasons,  it seems nice to have ONE BIG partition or at least a few large partitions.

I dislike excessive use of folders.

my current set up as all userdata with apps on a seperate partition (distinct from win 7 system which is less than 19gb and runs fine).  

some things will never be larger than a certain size (like server backup) so that makes sense to have separate partition.

I may do

new process =newp (all new stuff.  I will reformat this every two weeks and get data off of it; it will function as scratch and download disk

linux partition

and then prob server backup

and then although I haven't done this in forever I may put EVERYTHING (system, user data, )
OR

apps  and sys seperate

I may cluster media files (video and audio, of which their are 4 VERY distinct types.  external and internal).  on a same partition but I like one partiton JUST focused on that so I always know that will be full.

The problem with clumbing media files and apps on the same partition is I could easily installs tons of one kind and then it would be out of balance (too many apps, not enough room for audio and vido files, or vice versa).

bollocks.

I may do most all stuff on one main and then the new process, linux, and sys on seperates.  

By the way, no offense, but I think "just user folders" is about one of the most retarded, hackneyed, and stupifyingly dull answers anyone can provide.  It's about as trite as someone being like "go to the vet' when someone asks a question about their cat (another type of forum where I see a set of useless answers repeatedly).


It would take a long time to explain all the details of my organization system.  it's been years in the works of refining and debugging (with a lot of different operating systems and whatnot).  It transcends most all applications and is cross-platform (meaning it's not bound to a certain application, which is the wya any organization system should be).

But I few insights are 

ORIG is the original file obviously.  this is what I have to backup.  if something isn't ORIG than it's a backup of an orig.  

even all apps are not ORIG because they're implementations of the installers.   Most all installers (if not online) are local disc images and stored in their own installers_ORIG folder.  That may be a partiton, though, but that's actually completely unrelated to this 500GB.


I have to hink about what I would use this for.  Like, it would be really nice to have some internal media (that I recorded mainly audio files) and have that a set amount (With a partition.  Then I could always change that around if I wanted.  with new media files.

I could do that with folders but one folder could easily balloon and take the space of other things.

So the partitions are quota-setting and also the obvious necessary primary partition distinctions (like ext4 linux and ntfs windows different file formats).  Most all partitions will be ntfs though for filesystem.


I've spent a lot of years consolidating almost all types of data I have.  Again, I prob should (and sort of have) written a book on this.  "Called POPP: Progress and Organizational PRoductivity Principles".  If you want more detailed info, you should just buy the book!"


basically, I think clumping all videos (that you didn't make and your own creations, for exmample) in /home/USERNAME/'My Videos" is about one of the most idiotic things someone can do because the external video files are NOT YOURS, you didn't make them, you just burnt them, downloaded them, or purchased them.  so I keep that distinct.

I'm a computer scientist.  I may not know as much as some other peopel do about details of read-write location sectors, but I want to leanr a lot more.

I have over 20,000 pictures I've taken that have hteir own format string for naming and clear hierarchy in three folders.  


I guess what I have setup is too......idiosyncratic, odd, advanced, intelligent, insanely complex, peculiar, and/or different to get much insight into partitioning.



I've bene scrutinizing what didn't work.

on this 1TB I had 

random 20GB (prob intended to use that for linux, but never got around to that).

300gb for scratch PFFTT terrible  this was one extendd of a logical and I say terrible because I used about 40gb max of it.

meanily a 200gb I used for installers, and all "external" data and that had really good usage and thus should have been distributed better.

if I had 1TB internal instead of 500gb I know exactly how I would partiton (and using folders only with 1TB would be most assuredly the way of the imbecile). 

I think what I'm stressed about is I won't have neough space on the 500gb for EVERy core bit of useful data that I'd want so I'll have to be selective, which is fine.

I'm certianly compleaining, it's the most HD space I've ever had on a laptop and am overjoyed.


When I get my rig built I would have 3,820GB of data (but really <1TB of original data, most all of that is backups for which I have calendared safe system (if I didn't have the calendared safe system) I would be insanely anxious,but with the structured data protection everything is awesome.



it's more like "glee" from having this much HD space on a laptop and wanting to avoid probs.  I just want to immediately start transfering and installing things onto it but then I envision in a few weeks wishing I had a small linux partition or a small seperate scratch partition or something.

validateyourlife.com
and 
linuxgeedkoid.com

are sites where I touch on some of this.



I think one of hte most useful things I learned from a forum was that subsequent partitions have a slightly lower read-write time (or maybe it was access time) because of their location on the disk.


idk what to say my organization system would take many pages to explain thoroughly.  This was mainly brainstorming.


Anyways, if some iteration of this was said I agree with it that many small partitions without a very specific use usually results in wasted space.  But just one block-headed partition is obtuse and really crippling what you can do with (with multiple operating systems, and I REALLy like having a set scratch disk that can be frequently reformatted to deal with fragmentation from a lot of read/write to it).  

prob 

25 win
40 lin
30 newp
105 db
300 everything else.  hhmm I like having a set partition for media though so am tempted to do

300 to 200 apps and userdata 100 media.


No offense but this thread hasn't been much help.  This is not a problem though because I realize my brainstorming post was basically cryptic notes that I use all the time to easily refer to very distinct types of data.



anyways.  I'll 


one though I had was that Iv'e bene using linux and windows on a mac (which I loathe) for over the past year.  I realized that a lot of the partitioning may have bene because of that.  I still need to learn a lOT more about boot managers/loaders!! I know grub is linux.  What's windows' version and crap mac's version?  

But basically being on a computer where I can have JUST windows or JUST linux (optionally one OS) is pretty delightful.


I'm trying to discern how much of the multiple partitions was emotionally disconnecting from mac crap.  Soem of it was.  and I always needed at least two partitions to run non-mac os.  So anyways.  I am tempted jsut to use the raw one partition but think I'll want more options later.


I don't understand the obsession with folders.  If someone posts in a partition thread on a "hard drive" category, they don't really want to here about "folders".  any imbecile can make a folder and I'm (no offense) a bit insulted that someone would actually offer that as advice and genuinely think that it has value.


All that said.  I don't see how sharing details of my organizing system would help you provide insight into how I should parititon.

I had a huge sequence of threads a few months ago about partitioning the aforementioend 1TB.  A guy poped on the thread who had over 3TB and about 14 partitions.  That was really joyful and helpful and sparked some ideas (although I though much of his partitioning scheme was ludicrous).

I think more than 8 partitiosn is insane, but then again I coudl partition up one drive with 8 (if it were multiple terabytes) so combining internal and external I could see how total partitiosn coudl easily exceed 14.  



Umm  I'ts bascially just tinkering.  Last partitioning the partition distinctiosn were REALLY well designed (it's good to keep scratch disk separate.  someone suggested that on a forum and that made tons of hard disk health sense).  But in various partitioning schemes the size of the scratch disk, for example, was uselessly too small (it would fill up to quickly and then download errors or read-write errors) or too large, and unused. 

Maybe I'll post what I decided on later but it will be similar to what I originally brianstormed.

I''ve put SOOO much thought inot this.

My computer is my house.  It's where I live.  So someone who is building there hosue would probably approach partitioning hard drive and being organized about files the way I have. it's that important to me.


btw.  I just wrote this response sloppily (but whole-heartedly ) with a lot of spelling mistakes and didn't mean to offend anyone about the folders suggestion it's just that anyone can go shift+cntrl+n * 10, and have ten folders and ten seconds.  That's not complex and not really a useful response.  I think a comparable suggestion would be like someone inquring about how to do a certain part of a blueprint for a house their designign and then....someone goes...oh just use an apartment or something....or someone building a computer and then someone goes, oh just by a pre-built one.  That's not what the thread is about.  This entire thread is about partitions.  


Anyways, bookmark those links.  If you're interested in the idiosyncratic (but imho massivley efficient) organizing methods I have will likely have updates there.

cheers. thanks.









It wasn't my intention to be cryptic but i LIVE in a computer. Partitioning this (these) hard drives is like building a home. I have been refining a (extremely efficient and intelligent, but admittedly idiosyncratic and possibly eccentic, but it makes sense to me) organizing system for data for many years and it's undergone a lot of revisions and refinements. basically that was brainstorming.
I should be designing operating systems because that's basically the amount of detail that I'm going into. I am disgusted with the pre-defined folders in "home" folder. I need to learn more about boot loaders, read-write access of hard drive data etc. the SFH filesystems.

---

