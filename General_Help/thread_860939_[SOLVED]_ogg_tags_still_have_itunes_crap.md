---
title: "[SOLVED] ogg tags still have itunes crap"
date: 2008-07-16
forum: General Help
---

### Post by logos34 on 2008-07-16
I converted my apple lossless to ogg.  The tags look fine in amarok, Audacious and even **EasyTag**.  But when I look at them with vorbiscomment I see this:
> 
/music/John Coltrane/The Very Best Of John Coltrane$ **vorbiscomment -l** 04\ Like\ Sonny.ogg 
ALBUM=The Very Best Of John Coltrane
ARTIST=John Coltrane
COMPILATION=0
COMPOSER=John Coltrane
DATE=2000
DESCRIPTION=
DISCNUMBER=1
ENCODED BY=[COLOR=Red]iTunes v6.0.2.23[/COLOR]
GENRE=Jazz
[COLOR=Red]ITUNES_CDDB_IDS=11+83C5D53326A31780A6B222FB0660F7F7+707368
ITUNNORM= 000007B6 00000075 00006020 00001473 00009386 00050CC3 00007663 00006290 0001484A 0001DE82[/COLOR]
TEMPO=0 BPM
TITLE=Like Sonny
TRACKNUMBER=4

How do I get rid of the iTunes crap? And why does it show only here?

---

### Post by logos34 on 2008-07-16
nm...[This man page]("http://www.linuxcommand.org/man_pages/vorbiscomment1.html") may work (the current man docs on my machine do not explain it as well)

Still, this will take forever.  Is there another tag editor like EasyTag that will handle batch edits (recognize iTunes comments)?

---

### Post by logos34 on 2008-07-18
Ok, I figured out how to do batch edits of ogg tags to clean up 'iTunes' comment fields:

Use [vorbiscommentedit]("http://www.phonk.net/Gedachten/about-oggedit")

*Note: I still can't figure out how to run **vorbistagedit** and have it invoke gedit instead of nano (so I can use Search>'replace' option).  If anyone knows, please tell me!

Get the bash script [here]("http://www.phonk.net/Gedachten/vorbiscommentedit").  Save page as **vorbiscommentedit** in $HOME.

Make it executable:

$ **sudo chmod u+x vorbiscommentedit**

Run it:

$ **./vorbiscommentedit /path/to/music/files/*.ogg**

Here's a sample of what appears in nano text editor:

> ALBUM=The Very Best Of John Coltrane
ARTIST=John Coltrane
COMPILATION=0
DATE=2000
DESCRIPTION=
DISCNUMBER=1
 ENCODED BY=[COLOR=Red]iTunes v6.0.2.23[/COLOR]
GENRE=Jazz
TEMPO=0 BPM
~ COMPOSER
~ [COLOR=Red]ITUNES_CDDB_IDS[/COLOR]
~ TITLE
~ TRACKNUMBER* I already took out [COLOR=Red]ITUNNORM=[/COLOR] comment field, so the remaining differing ones are listed at bottom  preceded by '~'

-I take out '[COLOR=Red]iTunes v6.0.2.23[/COLOR]', and copy '[COLOR=Red]ITUNES_CDDB_IDS[/COLOR]' above (without '~') so it now looks like this:

> ALBUM=The Very Best Of John Coltrane
 ARTIST=John Coltrane
 COMPILATION=0
 DATE=2000
 DESCRIPTION=
 DISCNUMBER=1
**  ENCODED BY=**
 GENRE=Jazz
 TEMPO=0 BPM
**[COLOR=Black]ITUNES_CDDB_IDS=[/COLOR]**
~ COMPOSER
 ~ [COLOR=Red]ITUNES_CDDB_IDS[/COLOR]
 ~ TITLE
 ~ TRACKNUMBERCrl+O to save.  Now every track is like this:


> ALBUM=The Very Best Of John Coltrane
 ARTIST=John Coltrane
 COMPILATION=0
 DATE=2000
 DESCRIPTION=
 DISCNUMBER=1
  ENCODED BY=
 GENRE=Jazz
 TEMPO=0 BPM
**ITUNES_CDDB_IDS=**
 ~ COMPOSER
 ~ TITLE
 ~ TRACKNUMBERNow **remove** the common field '**ITUNES_CDDB_IDS=**'.  Ctrl+O to save.  The next time I reopen it, voila! the field is gone:

> ALBUM=The Very Best Of John Coltrane
ARTIST=John Coltrane
COMPILATION=0
DATE=2000
DESCRIPTION=
DISCNUMBER=1
  ENCODED BY=
GENRE=Jazz
TEMPO=0 BPM
~ COMPOSER
~ TITLE
~ TRACKNUMBERIf I want to specify the oggenc build used to transcode the original Apple lossless .m4a (.alac) files, then I add:

>   [COLOR=Black]ENCODED BY=[COLOR=Blue]Xiph.Org libVorbis I 20070622 (1.2.0)[/COLOR][/COLOR]or in the case of others:

  > [COLOR=Black]ENCODED BY=[/COLOR][COLOR=Blue]AO; aoTuV b5 [20061024] (based on Xiph.Org's libVorbis)[/COLOR]

---

