---
title: "Mounting problems"
date: 2008-12-26
forum: Hardware
---

### Post by cnaqe1 on 2008-12-26
I'm still having problems mounting my cdrom. I can't even burn cd or dvds. I've posted this problem a few times and got little response. I will give all the information needed. This is what I typed.

sudo lshw -C disk:

*-cdrom:0
description: CD-R/CD-RW writer
product: CD-RW CW-7585
vendor: MATSHITA
physical id: 2
bus info: scsi@1:0.0.0
logical name: /dev/cdrom
logical name: /dev/cdrw
logical name: /dev/scd0
logical name: /dev/sr0
version: 1.04
serial: [MATSHITACD-RW CW-7585 1.040
capabilities: removable audio cd-r cd-rw
configuration: ansiversion=5 status=nodisc


the dvd-rom drive says:

*-cdrom:1
description: DVD reader
physical id: 3
bus info: scsi@1:0.1.0
logical name: /dev/cdrom1
logical name: /dev/dvd1
logical name: /dev/scd1
logical name: /dev/sr1
capabilities: audio dvd
configuration: status=nodisc

Can anyone help me, please?

---

### Post by Databit on 2008-12-26
There are a couple of important questions in one of your previous post about this issue. What does your computer see as the cdrom and what is in your fstab (file that controls some mounting/automounting). 

Go to a terminal and copy and paste this line in there:
 cat /etc/fstab > ~/Desktop/fstab.txt;ls -R /media > ~/Desktop/medialist.txt


This will create 2 files on your desktop (a copy of your fstab and a directory listing of your cdrom. Copy and paste the contents of those files into a reply. 

Also what happens when you put a cd in the drive? Does it spin? Do you get errors? What types of cds have you tried? (Application, Audio, Video, DVD)

---

### Post by cnaqe1 on 2008-12-27
here's what you asked for:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=62220165-2186-4b1f-95b1-66aadd7371d4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=110ac2b9-496b-4aa1-9132-be855efa844e none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0


/media:
cdrom
cdrom0
cdrom1
disk
disk-1

/media/cdrom0:

/media/cdrom1:

/media/disk:
Azureus Downloads
Documents
Drum Lesson Videos
Incomplete
lost+found
Music
Programs
The Boondocks
Various Artist
Videos

/media/disk/Azureus Downloads:
Bad Boys(1995DvDrip).avi
Bad Boys 2(2003DvDrip).avi
Cars[2006]DvDrip[Eng]-aXXo
The Incredibles [Eng] [DVDrip] [DivX]-$am3e
Wall-E[2008]DvDrip-aXXo.avi

/media/disk/Azureus Downloads/Cars[2006]DvDrip[Eng]-aXXo:
Cars[2006]DvDrip[Eng]-aXXo.avi

/media/disk/Azureus Downloads/The Incredibles [Eng] [DVDrip] [DivX]-$am3e:
The Incredibles [Eng] [DVDrip] [DivX]-$am3e.avi

/media/disk/Documents:
broken-ride-patterns.pdf
Documents.odt
exercises.odt
Final Fantasy XII.odt
x-fill-solo-pattern.pdf

/media/disk/Drum Lesson Videos:
freedrumlessons._Drum_Rudiments_-_Learn_How_To_Play_All_40_Drum_Rudiments.flv
freedrumlessons._Folk_Rock_Drumming_Lesson_-_Free_Play-Along_Song.flv
freedrumlessons._Free_Bass_Drum_Techniques_Video_Drum_Lesson_Online_1.flv
freedrumlessons._Free_Bass_Drum_Techniques_Video_Drum_Lesson_Online.flv
freedrumlessons._Free_Drum_Play-Alongs_for_Rock_Jazz_and_Latin_Drumming.flv
freedrumlessons._Funk_Drumming_Lesson_-_Free_Play-Along_Song.flv
freedrumlessons._How_To_Play_Drums_with_a_Free_5-Minute_Video_Lesson_1.flv
freedrumlessons._How_To_Play_Drums_with_a_Free_5-Minute_Video_Lesson.flv
freedrumlessons._How_To_Tune_A_Snare_Drum_-_Free_Video_Drum_Lesson.flv
freedrumlessons._Improve_Your_Bass_Drum_Speed_with_these_Tips_and_Tricks.flv
freedrumlessons._Improve_Your_Double_Bass_Drumming_with_Drum_Beats.flv
freedrumlessons._Improve_Your_Double_Bass_Drumming_with_Drum_Fills.flv
freedrumlessons._Improve_Your_Double_Bass_Drumming_with_Warm-Ups.flv
freedrumlessons._Improve_Your_Drumming_with_Bass_Drum_Independence_Beats.flv
freedrumlessons._Improve_Your_Latin_Drumming_with_Bossa_Nova_Beats.flv
freedrumlessons._Improve_Your_Latin_Drumming_with_Rumba_Clave_Beats.flv
freedrumlessons._Improve_Your_Latin_Drumming_with_Son_Clave_Beats.flv
freedrumlessons._Improve_Your_Latin_Drumming_with_Songo_Drum_Beats.flv
freedrumlessons._Improve_Your_Rock_Drumming_Creative_Tom-Tom_Drum_Beats.flv
freedrumlessons._Improve_Your_Rock_Drumming_Unique_Half-Time_Drum_Beats.flv
freedrumlessons._Improve_Your_Rock_Drumming_with_Broken_Eighth_Note_Fills.flv
freedrumlessons._Improve_Your_Rock_Drumming_with_Broken_Sixteenth_Note_Fills.flv
freedrumlessons._Improve_Your_Rock_Drumming_with_Eighth_Note_Beats.flv
freedrumlessons._Improve_Your_Rock_Drumming_with_Eighth_Note_Fills.flv
freedrumlessons._Improve_Your_Rock_Drumming_with_Quarter_Note_Beats.flv
freedrumlessons._Improve_Your_Rock_Drumming_with_Quarter_Note_Fills.flv
freedrumlessons._Improve_Your_Rock_Drumming_with_Sixteenth_Note_Accent_Beats.flv
freedrumlessons._Improve_Your_Rock_Drumming_with_Sixteenth_Note_Accent_Fills.flv
freedrumlessons._Improve_Your_Rock_Drumming_with_Sixteenth_Note_Beats.flv
freedrumlessons._Improve_Your_Rock_Drumming_with_Sixteenth_Note_Fills.flv
freedrumlessons._Improve_Your_Rock_Drumming_with_Two_Handed_16th_Note_Beats.flv
freedrumlessons._Jazz_Drumming_Lesson_-_Free_Play-Along_Song_1.flv
freedrumlessons._Jazz_Drumming_Lesson_-_Free_Play-Along_Song_2.flv
freedrumlessons._Jazz_Drumming_Lesson_-_Free_Play-Along_Song.flv
freedrumlessons._Latin_Drumming_Lesson_-_Bossa_Nova_Play-Along_Song.flv
freedrumlessons._Latin_Drumming_Lesson_-_Songo_Play-Along_Song.flv
freedrumlessons._Learn_Double_Bass_Drumming_with_Free_Drum_Lessons.flv
freedrumlessons._Learn_Drum_Set_Theory_Notation_-_Free_Video_Lesson.flv
freedrumlessons._Learn_Essential_Drum_Related_Terms_1.flv
freedrumlessons._Learn_Essential_Drum_Related_Terms.flv
freedrumlessons._Learn_How_To_Choke_The_Sound_of_Cymbals.flv
freedrumlessons._Learn_How_To_Count_32nd_Notes_-_Drum_Theory_Lesson.flv
freedrumlessons._Learn_How_To_Count_Eighth_Notes_-_Drum_Theory_Lesson.flv
freedrumlessons._Learn_How_To_Count_Eighth_Note_Triplets_-_Drum_Theory_Lesson.flv
freedrumlessons._Learn_How_To_Count_Quarter_Notes_-_Drum_Theory.flv
freedrumlessons._Learn_How_To_Count_Rests_in_Drum_Notation.flv
freedrumlessons._Learn_How_To_Count_Sixteenth_Notes_-_Drum_Theory_Lesson.flv
freedrumlessons._Learn_How_To_Count_Sixteenth_Note_Triplets_-_Drum_Theory_Lesson.flv
freedrumlessons._Learn_How_To_Hold_Drumsticks_With_Proper_Grip_1.flv
freedrumlessons._Learn_How_To_Hold_Drumsticks_With_Proper_Grip.flv
freedrumlessons._Learn_How_To_Open_Close_The_Hi-Hats.flv
freedrumlessons._Learn_How_To_Play_Accents_With_Rim_Shots.flv
freedrumlessons._Learn_How_To_Play_Blues_Shuffle_Beats_on_the_Drums.flv
freedrumlessons._Learn_How_To_Play_Funk_Music_on_the_Drums.flv
freedrumlessons._Learn_How_To_Play_Ghost_Notes_On_The_Drums.flv
freedrumlessons._Learn_How_To_Play_Jazz_Drumming_Beats_1.flv
freedrumlessons._Learn_How_To_Play_Jazz_Drumming_Beats.flv
freedrumlessons._Learn_How_To_Play_Jazz_with_Free_Drum_Lessons.flv
freedrumlessons._Learn_How_To_Play_Latin_with_Free_Drum_Lessons.flv
freedrumlessons._Learn_How_To_Play_Lesson_25_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_Odd-Time_with_54_Drum_Beats.flv
freedrumlessons._Learn_How_To_Play_Odd-Time_with_74_Drum_Beats.flv
freedrumlessons._Learn_How_To_Play_Punk_Drum_Beats_on_the_Drum_Set.flv
freedrumlessons._Learn_How_To_Play_Rock_with_Free_Drum_Lessons.flv
freedrumlessons._Learn_How_To_Play_The_Basic_Flam_Stroke_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Basic_Jazz_Drumming_Pattern.flv
freedrumlessons._Learn_How_To_Play_The_Double_Drag_Tap_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Double_Paradiddle_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Double_Ratamacue_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Double_Stroke_Roll_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Dragadiddle_1_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Dragadiddle_2_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Drag_Ruff_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Eleven_Stroke_Roll_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Fifteen_Stroke_Roll_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Five_Stroke_Roll_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Flam_Accent_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Flamacue_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Flam_Drag_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Flam_Paradiddle-Diddle_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Flam_Paradiddle_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Flam_Tap_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Inverted_Flam_Tap_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Nine_Stroke_Roll_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Pataflafla_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Seven_Stroke_Roll_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Seventeen_Stroke_Roll_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Single_Dragadiddle_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Single_Drag_Tap_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Single_Flammed_Mill_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Single_Paradiddle-Diddle_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Single_Paradiddle_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Single_Ratamacue_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Single_Stroke_Four_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Single_Stroke_Roll_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Single_Stroke_Seven_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Six_Stroke_Roll_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Swiss_Army_Triplet_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Ten_Stroke_Roll_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Thirteen_Stroke_Roll_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Triple_Paradiddle_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Triple_Ratamacue_-_Drum_Rudiment.flv
freedrumlessons._Learn_How_To_Play_The_Triple_Stroke_Roll_-_Drum_Rudiment.flv
freedrumlessons._Learn_To_Play_A_Multiple_Bounce_Roll_Buzz_Roll_-_Drum_Rudiment.flv
freedrumlessons._Learn_To_Play_Creative_Jazz_Drumming_Fills.flv
freedrumlessons._Learn_To_Play_Crescendos_Decrescendos_On_the_Drums.flv
freedrumlessons._Learn_To_Play_Drums_with_a_7-Minute_Free_Video_Lesson_1.flv
freedrumlessons._Learn_To_Play_Drums_with_a_7-Minute_Free_Video_Lesson.flv
freedrumlessons._Learn_To_Play_The_Snare_Drum_With_Cross-Sticking.flv
freedrumlessons._Learn_To_Sizzle_The_Hi-Hats_For_Drumming_Dynamics.flv
freedrumlessons._Note_Value_Exercise_for_Drum_Set_Independence_Control.flv
freedrumlessons._Play_The_Drums_Better_With_Correct_Posture_1.flv
freedrumlessons._Play_The_Drums_Better_With_Correct_Posture.flv
freedrumlessons._Play_The_Drums_With_Groove_and_Dynamics.flv
freedrumlessons._Rock_Drumming_Lesson_-_Free_Play-Along_Song_1.flv
freedrumlessons._Rock_Drumming_Lesson_-_Free_Play-Along_Song_2.flv
freedrumlessons._Rock_Drumming_Lesson_-_Free_Play-Along_Song_3.flv
freedrumlessons._Rock_Drumming_Lesson_-_Free_Play-Along_Song_4.flv
freedrumlessons._Rock_Drumming_Lesson_-_Free_Play-Along_Song_5.flv
freedrumlessons._Rock_Drumming_Lesson_-_Free_Play-Along_Song_6.flv
freedrumlessons._Rock_Drumming_Lesson_-_Free_Play-Along_Song.flv
freedrumlessons._Simple_and_Effective_Drum_Set_Warm-Up_Exercises_1.flv
freedrumlessons._Simple_and_Effective_Drum_Set_Warm-Up_Exercises.flv
freedrumlessons._Snare_Bass_Drum_Comping_Exercises_for_Jazz_Drumming.flv
freedrumlessons._The_Secret_Drum_Lessons_10.flv
freedrumlessons._The_Secret_Drum_Lessons_11.flv
freedrumlessons._The_Secret_Drum_Lessons_12.flv
freedrumlessons._The_Secret_Drum_Lessons_13.flv
freedrumlessons._The_Secret_Drum_Lessons_14.flv
freedrumlessons._The_Secret_Drum_Lessons_15.flv
freedrumlessons._The_Secret_Drum_Lessons_1.flv
freedrumlessons._The_Secret_Drum_Lessons_2.flv
freedrumlessons._The_Secret_Drum_Lessons_3.flv
freedrumlessons._The_Secret_Drum_Lessons_4.flv
freedrumlessons._The_Secret_Drum_Lessons_5.flv
freedrumlessons._The_Secret_Drum_Lessons_6.flv
freedrumlessons._The_Secret_Drum_Lessons_7.flv
freedrumlessons._The_Secret_Drum_Lessons_8.flv
freedrumlessons._The_Secret_Drum_Lessons_9.flv
freedrumlessons._The_Secret_Drum_Lessons.flv
freedrumlessons._Use_Bass_Drum_Comping_To_Improve_Your_Jazz_Drumming.flv
freedrumlessons._Use_Snare_Drum_Comping_To_Improve_Your_Jazz_Drumming.flv
Introduction To Rudiments - Drum Lessons.flv
notation.wmv
sticktechnique.wmv
youtube.YouTube_-_Tony_Royster_Jr_live_playing_with_Jay_Z-_American_Gangster.flv
youtube.YouTube_-_Triple_Back_Beat_gospelchopscom.flv

/media/disk/Incomplete:
T-3071998-Jill Scott - Its The Way You Love Me.mp3
T-3307542-12 - Jill Scott - Celibacy Blues - The Real Thing Word And Sounds Vol. 3.mp3
T-3475730-Jill Scott - Ephiphany.mp3
T-3711117-Mystical sun - Salt tank (Ambient edit).mp3
T-4212576-Mystical - Bouncin' Back (Bumpin' Me Against the Wall).mp3
T-4838334-06 - Ball And Chain.mp3
T-5132449-Jill Scott - Gimme.mp3
T-5423104-Jill Scott - The Real Thing Words And Sounds Vol. 3 - 14 - Wanna Be Loved.mp3
T-5672262-Anthony Hamilton - Ain't Nobody Worryin' - 02 -  Southern Stuff.mp3
T-5710727-06-anthony_hamilton-fallin_in_love_again.mp3
T-5734444-Anthony Hamilton - Sista Big Bones.mp3
T-5826730-05-anthony_hamilton-stone_cold.mp3
T-5939754-Jill Scott - My Love.mp3
T-5965406-Jill Scott - Whenever You're Around.mp3
T-6058174-Jill Scott - Cross My Mind.mp3
T-6062270-Jill Scott - Beautifully Human - 06 - Cross My Mind.mp3
T-6221952-07-anthony_hamilton-trouble.mp3
T-6317944-Jill Scott - The Fact Is (I Need You).mp3
T-6644017-Anthony Hamilton - Ain't Nobody Worryin' - 11 - Never Love Again.mp3
T-7914752-13 All I.mp3
T-7967100-Jill Scott-Come See Me.mp3
T-8154787-Jill Scott - The Real Thing Words And Sounds Vol. 3 - 16 - Imagination_(crown_royale_suite)_(bonus_track).mp3
T-9512889-Anthony Hamilton- Pass Me Over.mp3

/media/disk/lost+found:

/media/disk/Music:
01 - Devin The Dude - In My Draws.mp3
01 - I Used To Love Someone.mp3
01 - Scarface - Intro.mp3
01 - Track 1.oga
01 Wu Tang Clan - Liquid Swords (1).m4a
02 - Devin The Dude - I Can't Make It Home.mp3
02 - Micah Stampley - Holy Visitation.mp3
02 ***** Poppin.mp3
02 Untouchable.m4a
03-anthony_hamilton-the_day_we_met.mp3
03 The Kingdom Is Coming (Reprise).wma
04-anthony_hamilton-diamond_in_the_rough.mp3
04 - Devin The Dude - Let Me Know It's Real.mp3
04 Don't Say What You Won't Do.mp3
04 - Georgie Parker.mp3
04 Idlewild Blue (Don't Chu Worry 'Bout Me).mp3
04 - J. Moss - I'm Not Perfect (Feat. Anthony Hamilton).mp3
04 - Micah Stampley - How He Loves My Praise.mp3
04 - Micah Stampley - No Compromise.mp3
04 Southside.m4a
05 - Anthony Hamilton - Coming Where Im from.mp3
05-anthony_hamilton-glad_u_called.mp3
05-anthony_hamilton-i_did_it_for_sho.mp3
06-anthony_hamilton-hard_to_breathe.mp3
06-devin_the_dude-everyday_(feat._kb).mp3
06 - Devin The Dude - Me, You.mp3
06-t-pain-suicide.mp3
07-devin_the_dude-get_high.mp3
07 For Real.m4a
07-ludacris_-_everybody_hates_chris_(co-starring_chris_rock).mp3
08-Hymn Medley- Fill My Cup Lord-I Need Thee Every Hour-Jonathan Nelson-Right Now Praise-Rock-320kbps.mp3
08 - West Angeles Cogic Mass Choir & Congregation - No Limit.mp3
09 Mary Jane.m4a
09_ Micah Stampley - NEVER LET YOU GO.mp3
10 Sellout.wma
10 - West Angeles Cogic Mass Choir & Congregation - I'm Gonna Praise Him.mp3
11 Because You Love Me (Reprise).wma
11 - Devin The Dude - I Need A Song.mp3
11 Smartz.m4a
12 - Devin The Dude - Stray.mp3
12 Faith.m4a
13 Fixed.wma
14 - Scarface - Outro.mp3
15 I Want You [Remix][-].wma
22. T-Pain - Bad Side.mp3
32 Wu Tang Clan - Who The **** Is 50.mp3
Andre 3000 - Behold A Lady.mp3
Andre 3000, Ludacris, Common - Oasis.mp3
Anthony Hamilton ft. Jaheim & Musiq Soulchild - Struggle No More.mp3
Biggie Smalls & Method Man - The What.mp3
Black Eyed Peas and 311 - Empire.mp3
Black Eyed Peas - Behind the Front - 11 - What Is It.mp3
Black Eyed Peas - Fallin' Up.mp3
Black Eyed Peas Ft Justin Timberlake - Where Is The Love.mp3
Black Eyed Peas - Gone Going .mp3
Black Eyed Peas - Joints and Jams.mp3
Black Eyed Peas - Karma.mp3
Black Eyed Peas - More.mp3
Black Eyed Peas - Pump It.mp3
Black Eyed Peas - Weekend.mp3
Bone Crusher - Back Up.mp3
Bonecrusher_Chamillionaire_Get up on IT.mp3
Bonecrusher - Crunk in the Club.mp3
Bonecrusher & David Banner - Wobble And Shake It.mp3
Bone Crusher - Fat man stomp.mp3
Bone Crusher Feat. Fabo (Of D4L) - Transform .mp3
Bonecrusher Ft. Busta Rhymes, Jadakiss, & Cameron - I Aint Never Scared Remix.mp3
Bonecrusher ft. Stat Quo - Gangster Baller.mp3
Bone Crusher - Goodie Mob - Hate Ourselves.mp3
BoneCrusher - Grippin The Grain.mp3
Bone Crusher - Neva Scared.mp3
Bonecrusher - Sound The Horn.mp3
Bone Crusher - Sound The Horn.mp3
Brandy ft Kanye West - Talk About Our Love.mp3
Cosmic slop shop - da bump.mp3
Crooked Stilo & Cypress Hill - Stepback.mp3
Cypress Hill - Black Sunday - 02 - I ain't Going Out Like That.mp3
Cypress Hill - Blunt Song.mp3
cypress hill, coolio, method man, ll cool j - space jam soundtrack - hit em high space jam.mp3
Cypress Hill & Eminem - Rap Superstar.mp3
Cypress Hill ft. Damien Marley - Ganja Bus.mp3
Cypress Hill f. Wu-Tang Clan - Killa Hilla Niggaz.mp3
Cypress Hill - Hand on the Pump.MP3
Cypress Hill - Hits From The Bong.mp3
Cypress Hill - How I Could Just Kill A Man.mp3
Cypress Hill - I Ain't Goin Out Like That.mp3
Cypress Hill - Illusions.mp3
Cypress Hill - Insane In The Brain.mp3
Cypress Hill - Insane In The Membrane.mp3
Cypress Hill - I Wanna Get High.mp3
Cypress Hill - Loco en el Coco (spanish).mp3
Cypress Hill - Lowrider.mp3
Cypress Hill - Low Rider.mp3
Cypress Hill - Maryjane.mp3
cypress hill - Puppet Master.mp3
Cypress Hill - Rock Superstar(1).mp3
Cypress Hill - Rock Superstar.mp3
Cypress Hill - Roll It Up, Light It Up, Smoke It Up.mp3
cypress hill - Sawed Off Shotgun.mp3
Cypress Hill - Shoot 'em Up (juice soundtrack).mp3
Cypress Hills - Illusions.mp3
Cypress Hill - Southland Killers.mp3
Cypress Hill - Steel Magnolia.mp3
Cypress Hill - Tequila Sunrise.mp3
Cypress Hill - Till Death Do Us Part - 03 - Latin Thugs.mp3
Cypress Hill - Weedman.mp3
Cypress Hill - When the **** Goes Down.mp3
Devin the Dude - Doobie Ashtray.mp3
Devin The Dude - Fa Sho.mp3
Devin The Dude Ft Andre 3000 & Snoop Dogg - what a job.mp3
Devin The Dude ft. Snoop Dogg & Andre 3000 - What A Job.mp3
Devin the Dude- I Don't Chase 'Em.mp3
Devin The Dude - It's A Shame.mp3
devin the dude - just chillin.mp3
Devin The Dude - Lacville 79.mp3
Devin The Dude - Landing Gear - 03. Think' Boutchu.mp3
Devin The Dude - Landing Gear - 05. El Grande Nalgas.mp3
Devin The Dude - Landing Gear - 10. Your Kinda Love.mp3
Devin The Dude - Payin For *****.mp3
Devin the Dude- Reefer And Beer.mp3
Devin The Dude - Smoke Sessions Vol. 1 - 02 - If I Did A Mixtape.mp3
Devin the Dude - Too Cute.mp3
Devin The Dude - To Tha X-Treme - 02 - Right Now.mp3
Devin the Dude - To Tha X-Treme - Anythang.mp3
Devin The Dude - To Tha X-Treme (Screwed & Chopped by.OG Ron.mp3
Devin the Dude - To Tha X-Treme - She's Gone.mp3
devin the dude - waiting to inhale - 04 - i hope i dont get sick_a_dis-aBc.mp3
Devin the Dude - Waiting to Inhale - 06 - Broccoli & Cheese.mp3
Devin the Dude - Waiting to Inhale - 09 - Lil' Girl Gone.mp3
Devin The Dude - Waiting To Inhale - 11 - just_because.mp3
Devin The Dude - Waitin' To Inhale - 02 - She Want That Money.mp3
Devin The Dude - Waitin' To Inhale - 07 - Boom II.mp3
Devin The Dude - Waitin' To Inhale - 10 - No Longer Needed Here.mp3
Devin The Dude - Waitin' To Inhale - 13 - Somebody Else's Wife.mp3
Devin the Dude - Waitin To Inhale - 16 - Nothin To Roll With.mp3
Devin the Dude- Who's That Man, Moma.mp3
DJ Felli Fel Ft. Ne-Yo & Fabolous & Kanye West & Jermaine Dupri - The Finer Things.mp3
DJ Khaled Ft. Kanye West & T-Pain - Go Hard..(Trackfiends.net).mp3
Dr Dre Method Man Redman - Bang Bang (Remix).mp3
E-40 - 03 - Da Bumble.mp3
E 40 and the Click - Wolf Tickets.mp3
E40 and TooShort - Keep Hustlin'(1).mp3
E-40, B Legit - Carlos Rossi.mp3
e40 & b-legit - sideways.mp3
E40, Bohagan, & Lil Scrappy - ***** Niggaz.mp3
E40-Captian Save Hoe.mp3
E-40 - Dump, Bust, Blast.mp3
E40 feat Mack 10 & Ant Banks - Can't Stop.mp3
E-40 f Fabolous - Automatic.mp3
E40 Ft. Nate Dogg - Nah Na.mp3
E40 ft. SPM - Henessy.mp3
E40 ft Tpain - you and dat booty                            .mp3
E40, Game, Kanye West - tell me when to go remix.mp3
E40-Gasoline.mp3
E-40 -  Go Hard Or Go Home.mp3
E40 -- Mustard & Mayonaise.mp3
E40 - Rep Your City.mp3
E-40 - Slangin Yayo.mp3
E-40, Spice 1, Celly Cell, Tupac - Dusted and Disgusted .mp3
E-40 - Sprinkle Me.mp3
E40 - Things'll Never Change.mp3
E40, TooShort & K-Ci - Rappers Ball.mp3
Freestyle #1 Eminem Wu-tang clan Jay Z Tupac 112 Beastie Boys Fugees P. Diddy Eve DMX Ja Rule Snoop Dogg Dr Dre The Roots Common Mos Def The Pharcyde NERD.mp3
Girl You Know Remix.mp3
Greg Street ft. Nappy Roots - Good Day.mp3
idlewild soundtrack.mp3
I Get High.mp3
INSTRUMENTALS Nappy_Roots-Awnaw_(Instrumental_Version).mp3__________outkast_ludacris_master_p_juvenile_mystikal_lil_bow_wow_nelly_bubba_sparxx_snoop_dogg_tupac.mp3
Instrumental - The Roots Ft Erykah Badu - You Got Me (Instrumental).mp3
Jay-Z and The Roots- Heart of the City (Ain't No Love)-MTV Unplugged.mp3
Jay-Z f. Kanye West - The Bounce.mp3
Jay-Z Ft. Scarface and Benie Segal - Guess Who's Back.mp3
Jill Scott - A Long Walk (Live Groove).mp3
Jill Scott - Beautifully Human - 05 - Spring Summer Feeling.mp3
Jill Scott - Beautifully Human - 06 - Cross My Mind.mp3
Jill Scott- Comes To The Light.mp3
Jill Scott - Golden.mp3
Jill Scott - Whatever, Whenever.mp3
Kanya West - Jesus Walks.mp3
Kanye West - 808s & Heartbreak - 01 - Say You Will.mp3
Kanye West - 808s & Heartbreak - 06 - Paranoid.mp3
Kanye West  - Addiction.mp3
Kanye West ft Daft Punk - Stronger.mp3
Kanye West ft. John Legend - I Used To Love You.mp3
Kanye West ft Lil Wayne - See You In My Nightmares.mp3
Kanye West ft. R. Kelly - Flashing Lights (Remix).mp3
Kanye West ft. T-Pain - Heartless.mp3
Kanye West ft. T-Pain - The Good Life(1).mp3
Kanye West ft. T-Pain - The Good Life.mp3
Kanye West ft Young Jeezy - Amazing.mp3
Kanye West  - Golddigger.mp3
Kanye West - Graduation - 09 - Flashing Lights (Ft. Dwele).mp3
Kanye West - Graduation - Bittersweet ft. John Mayer.mp3
kanye west - graduation - homecoming.mp3
Kanye West - Graduation - Stronger.mp3
Kanye West - Heard'em Say.mp3
Kanye West - Heartless.mp3
Kanye West - Love Lockdown.mp3
Kanye West - Love Lockdown - NEW.mp3
Kanye West - The Good the Bad the Ugly.mp3
Kanye West - We Are The Champions (Remix).mp3
Kayne West- All falls down.mp3
Kayne West -  through the wire.mp3
Keek Da Sneek - Supa Hyphy.mp3
Kid Sister feat. Kanye West - Pro Nails.mp3
KoRn, Limp Bizkit, Eminem, Sevendust, Slipknot, Incubus, Dope, POD, Cypress Hill, Orgy, Static X, Powerman 5000, Rob Zombie & System Of A Down-Ice on fire.mp3
Lil John Ft E40 - Snap ya fingerss.mp3
Little Girl Gone Ft. Lil' Wayne, Bun-B, Tami Latrell & Tony Mac - Devin The Dude.mp3
Ludacris - Been Puttin On.mp3
Ludacris - Blueberry Yum Yum.mp3
Ludacris- Blueberry Yum Yum .mp3
Ludacris - Cadillac Grills.mp3
Ludacris - Celebrity Chick (Feat. Chingy, Small World & Steph Jones).mp3
Ludacris feat. Chris Brown & Sean Garrett - What Them Girls Like.mp3
Ludacris Feat Jay-Z & Nas - I Do It For Hip Hop.mp3
Ludacris_feat._T-Pain_-_One_More_Drink_-_HotNewHipHop.com.mp3
Ludacris Feat. T-Pain - One More Drink.mp3
Ludacris ft. Field Mobb - Georgia.mp3
Ludacris ft Floyd Mayweather - Undisputed (Dirty).mp3
Ludacris ft. Lil' Flip - **** You.mp3
Ludacris Ft Lil Wayne - Last Of A Dying Breed.mp3
Ludacris Ft. Mary J. Blige - Runaway Love.mp3
Ludacris ft. The Game & Willy Northpole - Call Up The Homies (dirty)(1).mp3
Ludacris ft. Twista & Jagged Edge - Freaky Thangs(1).mp3
Ludacris Ft. Young Jeezy - Grew Up A ******* Screw Up.mp3
Ludacris-Ludachristmas.mp3
Ludacris - Move Bitch.mp3
Ludacris - Number One Spot.mp3
Ludacris & Pharrell - Money Maker.mp3
Ludacris - Politics Obama Is Here.mp3
Ludacris - Roll Out.mp3
Ludacris - Southern Hospitality.mp3
Ludacris - Splash Waterfalls.mp3
Ludacrist - Cadillac Grills .mp3
Ludacris - Theater Of The Mind - Look What I Got .mp3
Ludacris - Theater of the Mind - Stay Together.mp3
Ludacris - The Potion.mp3
Ludacris - Welcome To Atlanta.mp3
Ludacris - Whats Your Fantasy.mp3
Ludacris - When I Move You Move.mp3
Ludacris - Youz A Hoe.mp3
Lupe Fiasco f. Kanye West, Pharrell - US Placers.mp3
Method Man feat DAngelo- Breakups 2 Makeups.mp3
method man & redman - Lets Get Dirty.mp3
Method Man- Wu-Tang Clan- M-E-T-H-O-D Man.mp3
Micah Stampley 14 - Sovereign God.mp3
Micah Stampley - 5 - You Are Lord.mp3
Micah Stampley - A Fresh Wind - 01 - We Lift You Up.mp3
Micah Stampley - A Fresh Wind - 06 - Another Place.mp3
Micah Stampley - Always Remember.MP3
Micah Stampley - Another Place.wma
Micah Stampley - Corinthian Song.MP3
Micah Stampley - Draw Me Close.MP3
Micah Stampley - Holiness (Take My Life).mp3
Micah Stampley - I Believe.mp3
Micah Stampley - Lend Me Your Song.MP3
Micah Stampley - Let it Rise.mp3
Micah Stampley - Solid Rock.MP3
Micah Stampley - The Kingdom Is Coming (Reprise).mp3
Micah Stampley - Unfailing Love.wma
Micah Stampley- War Cry.mp3
Micah Stampley - We Lift You Up.mp3
Micah Stampley - Worthy To Be Praised.mp3
Micah Stampley- Yes.mp3
Mos Def, The Roots & Common - Hurricane.mp3
Myron Williams
mystical and ludacris - move bitch get out the way.mp3
Mystikal - OutKast - Neck uv da Woods.mp3
Nappy Roots - All My Life Been Poor.mp3
Nappy Roots - Aw Naw.mp3
Nappy Roots Ft. Anthony Hamilton - Sick and Tired.mp3
Nappy Roots - Hustla (Dirty Version) outkast ludacris master p juvenile mystikal lil bow wow nelly bubba sparks.mp3
nappy roots - Smokin and Drinkin.mp3
Nas ft Wu-Tang Clan - My War.mp3
Old School Rap - Cypress Hill & House of Pain - Jump Around.mp3
Outcast - Hey Ya.mp3
Outcast - I Like the Way You Move.mp3
Outcast - So Fresh and So Clean.mp3
Outcast - The Whole World.mp3
outkast-atliens.MP3
OutKast - ATLiens - Two Dope Boys (In a Cadillac).mp3
OutKast - Bowtie (feat. Sleepy Brown & Jazze Pha).mp3
Outkast - Idlewild - 01 - Intro.mp3
Outkast - Idlewild - 14 - Call The Law.mp3
Outkast - Idlewild - 15 - Bamboo & Cross (Interlude).mp3
Outkast - Idlewild - 19 - PJ & Rooster.mp3
Outkast - Idlewild - 22 - You're Beautiful (Interlude).mp3
Outkast - Idlewild - 22 - Youre_Beautiful.mp3
Outkast - Idlewild - 25 - A Bad Note.mp3
Outkast - Idlewild Blues.mp3
Outkast - Idlewild - PJ & Rooster.mp3
Outkast - Idlewild Soundtrack - Idlewild Blue (Don'tchu Worry-Bout Me).mp3
Outkast - Idlewild - The Soundtrack - Come Back 2 Me.mp3
Outkast - Idlewild - The Soundtrack - La La La.mp3
Outkast - Idlewild - The Soundtrack - Old Dayz.mp3
Outkast - Idlewild - The Soundtrack - Rebel Flag.mp3
Outkast - Idlewild - The Soundtrack - Romeo N Juliet.mp3
Outkast - Idlewild - The Soundtrack - Solder Status.mp3
Outkast - Idlewild - The Soundtrack - Why O Why.mp3
Outkast, Lil' Wayne & Snoop Dogg - Hollywood Divorce.mp3
Outkast - Morris_Brown (DIRTY).mp3
Outkast - Movin' Cool (The After Party).mp3
Outkast- Mrs. Jackson.mp3
Outkast - Roses.mp3
Outkast - Southernplayalistic.mp3
Outkast-The_Mighty_O.mp3
Outkast - The Whole World.mp3
rap-Instrumentals - Wu Tang Clan - Triumph.mp3
Relax - Jill Scott & Mos Def - Love Rain.mp3
Rusted Roots - Ecstasy.mp3
rusted roots - Send Me On My Way (Ice Age Soundtrack).mp3
Scareface featTupac - Smile.mp3
Scareface ft Kelly Price - Heaven.mp3
Scareface- someday.mp3
Scarface - 14 - In My Time - The Last Of A Dying Breed.mp3
Scarface Dr. Dre, Ice Cube & Too Short - Gameover.mp3
Scarface - Fix, The - 02 - Safe.mp3
Scarface ft. Trey Songz - Girl you Know (Remix).mp3
Scarface - In And Out.mp3
Scarface - In & Out.mp3
Scarface & Jay-Z & Beanie Seigel - Guess Who's Back (dirty).mp3
Scarface- Last of a Dying Breed- 07 -feat Dogg Pound - OG to me.mp3
Scarface - Last Of A Dying Breed - Sorry 4 What.mp3
Scarface- Last of a Dying Breed - The Gangsta ****.mp3
Scarface - On My Block.mp3
Scarface - The Fix - 01 - The Fix.mp3
Scarface - The Fix - 03 - In Cold Blood.mp3
Scarface - The Fix - 07 - What Can I Do Ft Kelly Price.mp3
Scarface - The Fix - 08 - In Between Us Ft Nas.mp3
Scarface - The Fix - 09 - Someday Ft Faith Evans.mp3
Scarface - The Fix - 12 - I Aint The One.mp3
Scarface - The Fix - 15 - Bonus Track -  Get Out (Feat. Jay-Z Xtra Track).mp3
Scarface - The G Code2.mp3
Scarface - The G Code.mp3
Scarface - The Untouchable - 03 - No Warning.mp3
Scarface - The Untouchable - 07 - For Real.mp3
Scarface - The Untouchable - 11 - Smartz.mp3
Tech n9ne - Imma Tell.mp3
Tech N9ne - Slacker.mp3
Tech Nine - Absolute Power.mp3
Tech Nine - Caribou Lou.mp3
Tech Nine feat. Eminem - Three.mp3
Tech Nine ft.c4 - Testin'.mp3
Tech Nine ft. Eminem, City Clay, Stagga Lee, Nelly, 50 Cent, Sairai, Jay-Z, Pharrell, Haystack, Chingy - I'm A Playa (Remix).mp3
Tech Nine - I'm a Beast.mp3
The Black Eyed Peas - My Humps (DJ Scotty B Remix) (Funkymix 90) 124 BPM.mp3
The Roots - All Night Long (ft. Common & Erykah Badu).mp3
The Roots- Don't Say Nuthin.mp3
The Roots & Erikah Badu - Baby You Got Me.mp3
The Roots  - (Feat Erykah Badu And Jill Scott) - You Got Me.mp3
The Roots feat. Mos Def - Double Trouble.mp3
The Roots ft. Jill Scott - You Got Me.mp3
The Roots ft. Talib Kweli - Rolling With Heat (The OC Soundtrack).mp3
The Roots - Get Busy.mp3
The Roots - Lazy Afternoon.mp3
The Roots - Rising Up (Featuring Wale & Chrisette Michele).mp3
The Roots - Rising Up ft. Chrisette Michelle, Wale.mp3
The Roots - The Next Movement.mp3
T.I feat. Kanye West, Jay-Z & Lil Wayne - Swaggar Like Us.mp3
T-Pain-Calm_The_****_Down_(Unreleased).mp3
T-Pain - Epiphany - 04 - Show U How.mp3
T-Pain - Epiphany - 08 - Back Seat Action.mp3
T-Pain - Epiphany - 11 - Yo Stomach.mp3
T-Pain feat. Akon - Bartender.mp3
T-Pain Feat. Akon - Bartender.mp3
T-Pain - Freeze Ft Chris Brown.mp3
T-pain ft. Lil wayne-Can't believe it.mp3
T-Pain-Put It Down .mp3
T-Pain- Sounds Bad.mp3
T-Pain(Thr33 Ringz) - Digital(ft. Tay Dizm).mp3
T-Pain- Tipsy.mp3
T-Pain - Up & Down - HotNewHipHop.com.mp3
Tupac & Scarface - Smile.mp3
Twista - **** Dr Dre, Snoop, Eminem, Warren G & Nate Dogg wu- tang clan,biggie, mobb deep,fugees, casidy,cypress hill , jay z ,dmx,nwa,gza,rza.ghostface killa,.mp3
UGK ft Outkast - Int'l players anthem (i choose you) (explicit_version).mp3
Unknown Artist
Will Smith ft. Ludacris - Party Starter.mp3
Wu-tang Clan - '97 Mentality.mp3
Wu Tang Clan - Bring The Rukus.mp3
Wu Tang Clan - Can It Be All So Simple.mp3
Wu-Tang Clan - Can't It All Be So Simple.mp3
Wu Tang Clan - Cocaine.mp3
Wu-Tang Clan - Concrete Jungle.mp3
Wu Tang Clan - CREAM.mp3
WuTang Clan - Da Mystery of Chessboxing - Enter The Wu-Tang- 36 Chambers - 06.mp3
Wu-Tang Clan - Enter the Wutang (36 chambers) - 05 - can it be all so simple.mp3
Wu-Tang Clan f. ODB - Shimmy Shimmy Ya.mp3
Wu Tang Clan - Freestyle  feature Old Dirty *******,  Eminem, DMX, Nas, Busta Rhymes, Gza, Jay-Z, Big Pun & Snoop Dogg.mp3

/media/disk/Music/Myron Williams:
Made To Worship

/media/disk/Music/Myron Williams/Made To Worship:
01 - Made to Worship (Interlude).oga
02 - King of Kings.oga
03 - I Can Only Imagine.oga

/media/disk/Music/Unknown Artist:
Unknown Title

/media/disk/Music/Unknown Artist/Unknown Title:
01 - Track 1.oga
02 - Track 2.oga
03 - Track 3.oga
04 - Track 4.oga
05 - Track 5.oga
06 - Track 6.oga
07 - Track 7.oga
08 - Track 8.oga
09 - Track 9.oga
10 - Track 10.oga
11 - Track 11.oga
12 - Track 12.oga
13 - Track 13.oga
14 - Track 14.oga

/media/disk/Programs:
flashplayer-installer
gobuntu-7.10-alternate-i386.iso
kubuntu-8.10-desktop-i386.iso
libflashplayer.so
xubuntu-8.10-desktop-i386.iso

/media/disk/The Boondocks:
Boondocks - 08 - The Real (pimp my ride).avi
Boondocks Season 2 Episode 6 - Attack of the Killer Kung Fu Wolf Bitch (Part 1)(1).mp4
Boondocks- The Corner.mp4
Boondocks-The Santa Stalker.mp4
Boondocks - The Trial of R Kelly.mp4
Little Big Town - Boondocks.mp4
tb-s2e01-xvid.avi
tb-s2e02-xvid.avi
tb-s2e03-xvid.avi
tb-s2e04-xvid.avi
tb-s2e05-xvid.avi
tb-s2e06-xvid.avi
tb-s2e07-xvid.avi
tb-s2e08-xvid.avi
tb-s2e09-xvid.avi
tb-s2e10-xvid.avi
tb-s2e11-xvid.avi
tb-s2e12-xvid.avi
tb-s2e13-xvid.avi
tb-s2e14-xvid.avi
tb-s2e15-xvid.avi
The_Boondocks_101_The_Garden_Party_[Moonsong].avi
The_Boondocks_102_The_Trial_of_R._Kelly_[Moonsong].avi
The_Boondocks_103_Guess_Hoe's_Coming_to_Dinner_[Moonsong].avi
The_Boondocks_104_Granddad's_Fight_[Moonsong].avi
The_Boondocks_105_My_Date_with_the_Health_Inspector_[Moonsong].avi
The_Boondocks_106_The_Story_of_Gangstalicious_[Moonsong].avi
The_Boondocks_107_A_Huey_Freeman_Christmas_[Moonsong].avi
The_Boondocks_108_The_Real_[Moonsong].avi
The Boondocks 109 The Return of the King [Moonsong].avi
The Boondocks 110 The Itis [Moonsong].avi
The Boondocks 111 Let's Nab Oprah [Moonsong].avi
The Boondocks 112 Riley Wuz Here [Moonsong].avi
the_boondocks_113_wingmen_[moonsong].avi
The Boondocks 114 The Block is Hot [Moonsong].avi
The Boondocks 115 The Passion of Rev. Ruckus [Moonsong].avi
The Boondocks - 1x01 - The Garden Party1.avi
The Boondocks - 1x02 - The Trail of Robert Kelly.avi
The Boondocks - 1x03 - Guess Hoe-s Coming to Dinner.avi
The Boondocks - 1x04 - Grandpa-s Fight.avi
The Boondocks - 1x05 - A Date with the Health Inspector.avi
The Boondocks - 1x06 - The Story of Gangstalicious.avi
The Boondocks - 1x07 - A Huey Freeman Christmas.avi
The Boondocks - 1x08 - The Real.avi
The Boondocks - 1x09 - Return of the King.avi
The Boondocks - 1x10 - The Itis.avi
The Boondocks - 1x11 - Let-s Nab Oprah.avi
The Boondocks - 1x12 - Riley Wuz Here.avi
The Boondocks - 1x13 - Wingman.avi
The Boondocks - 1x14 - The Block is Hot.avi
The Boondocks - 1x15 - The Passion of Reverned Ruckus.avi
The Boondocks - Hunger Strike (Ep 14 Season 2) (iPod and PSP mp4 Format).mp4
The.Boondocks.S02E01....Or Die Trying.avi
The.Boondocks.S02E02.Tom, Sarah And Usher.avi
The.Boondocks.S02E03.Thank You For Not Snitching.avi
The.Boondocks.S02E04.Stinkmeaner Strikes Back.avi
The.Boondocks.S02E05.The Story Of Thugnificent.avi
The.Boondocks.S02E06.Attack Of The Killer Kung-Fu Wolf Bitch.avi
The.Boondocks.S02E07.Shinin'.avi
The.Boondocks.S02E08.Ballin.avi
The.Boondocks.S02E09.Invasion Of The Katrinians.avi
The.Boondocks.S02E10.Home Alone.avi
The.Boondocks.S02E11.The N-Word.avi
The.Boondocks.S02E12.The Story Of Catcher Freeman.avi
The.Boondocks.S02E13.The Story Of Gangstalicious Part 2.avi
The.Boondocks.S02E14.The Hunger Strike.avi
The.Boondocks.S02E15.The Uncle Ruckus Reality Show.avi
The Boondocks - Season 01 Episode 10 - The Itis.avi
The Boondocks - Season 1 - Episode 10 - The Itis.mp4
The Boondocks - Season 2 - Episode 10 - Home Alone.avi
The Boondocks - Season 2 - Episode 11 - The S-Word.mp4
The Boondocks - Season 2 - Episode 4 - The Return of Stinkmeaner [DJCoBi](1)(1).mp4
The Boondocks - Season 2 - Soul Plane(1).mp4
The Boondocks - Uncle Rukus Reality Show (Ep 15 Season 2) (iPod and PSP mp4 Format).mp4
The.Dark.Knight[2008]DvDrip-aXXo.avi
The.Incredible.Hulk[2008]DvDrip-aXXo.avi
The.Matrix.Revolutions-2004 DVDRip.Xvid.avi

/media/disk/Various Artist:
Unknown Title

/media/disk/Various Artist/Unknown Title:
02 - Track 2.oga
03 - Track 3.oga
04 - Track 4.oga
05 - Track 5.oga
06 - Track 6.oga
07 - Track 7.oga
08 - Track 8.oga
09 - Track 9.oga
10 - Track 10.oga
11 - Track 11.oga
12 - Track 12.oga
13 - Track 13.oga
14 - Track 14.oga
15 - Track 15.oga
16 - Track 16.oga

/media/disk/Videos:
Bangkok.Dangerous[2008]DvDrip-aXXo.avi
Batman - The Dark Knight(DVDRIP)V.O 2008.avi
Casino.Royale[2006]DvDrip[Eng]-aXXo.avi
Desperado.avi
dmd-thewomen.avi
Eagle.Eye[2008]DvDrip-aXXo.avi
Get Smart[2008]DvDrip[Eng]-FXG.avi
God father part I.avi
Godfather part II.avi
Godfather part III.avi
Hellboy.2-The.Golden.Army[2008]DvDrip-aXXo.avi
Iron.Man[2008]DvDrip-aXXo.avi
James Bond Quantum of Solace TS XviD Full English Audio- Sync Fixed- Lynks.avi.avi
Kung.Fu.Panda[2008]DvDrip-aXXo.avi
Madagascar[2005]DvDrip-aXXo.avi
Ocean's.11[2001]DvDrip[Eng]-aXXo.avi
Ocean's.12[2004]DvDrip[Eng]-aXXo.avi
Ocean's.13[2007]DvDrip[Eng]-aXXo.avi
Once Upon A Time In Mexico.avi
Punisher.War.Zone.2008.TS.XviD-LTRG.avi
Righteous Kill[2008]DvDrip[Eng]-FXG.avi
Sin City[2005]DvDrip AC3[Eng]-FXG.avi
Traitor[2008]DvDrip-aXXo.avi
vuze
Wanted[2008]DvDrip[Eng]-FXG.avi

/media/disk/Videos/vuze:
azureus
Azureus2.jar
ChangeLog.txt
GPL.txt
installer.log
plugins
README.txt
swt.jar
TOS.txt
updateAzureus
vuze
vuze.png

/media/disk/Videos/vuze/plugins:
azplugins
azrating
azupdater
azupnpav

/media/disk/Videos/vuze/plugins/azplugins:
azplugins_2.1.6.jar

/media/disk/Videos/vuze/plugins/azrating:
azrating_1.3.1.jar

/media/disk/Videos/vuze/plugins/azupdater:
azupdaterpatcher_1.8.8.jar
azureus.sig
plugin.properties
Updater.jar

/media/disk/Videos/vuze/plugins/azupnpav:
azupnpav_0.2.2.jar
plugin.properties

/media/disk-1:
Images
Kanye West  - Addiction.mp3
Outkast - Idlewild - The Soundtrack - Rebel Flag.mp3
Outkast - Idlewild - The Soundtrack - Solder Status.mp3
Scarface - The Untouchable - 03 - No Warning.mp3
Scarface - The Untouchable - 07 - For Real.mp3
Sounds
SThumbDB.tdb
Tech n9ne - Imma Tell.mp3
Tech Nine - I'm a Beast.mp3
Videos

/media/disk-1/Images:
Photos

/media/disk-1/Images/Photos:

/media/disk-1/Sounds:
01 - Scarface - Intro.mp3
11 Smartz.m4a
12 Faith.m4a
14 - Scarface - Outro.mp3
BoneCrusher - Grippin The Grain.mp3
Crazy.dcf
ImMe.dcf
Outkast - Idlewild - 19 - PJ & Rooster.mp3
Scareface ft Kelly Price - Heaven.mp3
Scareface- someday.mp3
Scarface - 14 - In My Time - The Last Of A Dying Breed.mp3
Scarface Dr. Dre, Ice Cube & Too Short - Gameover.mp3
Scarface - Fix, The - 02 - Safe.mp3
Scarface ft. Trey Songz - Girl you Know (Remix).mp3
Scarface - In & Out.mp3
Scarface & Jay-Z & Beanie Seigel - Guess Who's Back (dirty).mp3
Scarface- Last of a Dying Breed- 07 -feat Dogg Pound - OG to me.mp3
Scarface - Last Of A Dying Breed - Sorry 4 What.mp3
Scarface- Last of a Dying Breed - The Gangsta ****.mp3
Scarface - On My Block.mp3
Scarface - The Fix - 01 - The Fix.mp3
Scarface - The Fix - 08 - In Between Us Ft Nas.mp3
Scarface - The Fix - 09 - Someday Ft Faith Evans.mp3
Scarface - The Fix - 12 - I Aint The One.mp3
Scarface - The Fix - 15 - Bonus Track -  Get Out (Feat. Jay-Z Xtra Track).mp3
Suffocate.dcf
TakeYouDown.dcf

/media/disk-1/Videos:
Videos

/media/disk-1/Videos/Videos:

When i put a cd or dvd in it mounts but it doesn't read blank cd's or dvd's. Media/disk-1 is my cell phone.

---

