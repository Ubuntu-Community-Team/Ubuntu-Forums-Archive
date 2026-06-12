---
title: "Only 2 softwares remainning"
date: 2008-09-25
forum: General Help
---

### Post by ExportA on 2008-09-25
Hi all, I'm a web developper and I would love to use Ubuntu for my everyday work.  All my daily apps have been replaced with free alternatives running under linux ... all except three.

I've searched and searched and didn't found anything that could replace them.

- Adobe Photoshop
- Ultra-Edit
- Total Video Converter

I have tried Gimp, but for someone who use Photoshop since v3.0, I need something really close to it to get a small learning curve.  As for Ultra-Edit, I tried a lot of editors, but no one seems as perfect as UE.  For total video converter, I only need a media converter that support All to All conversion, even supporting Flash FLV and mp3 conversions.

Anyone of you has suggestions?

Thanks a lot

---

### Post by Idefix82 on 2008-09-25
There is a version of Gimp which is supposed to have an interface similar to Photoshop, it's called GimpShop. It's not in the standard repositories though, you might have to add another repository. Have a look here:
[//http://www.gimpshop.com/]("//http://www.gimpshop.com/")

As for the editor: GEdit is a fantastic editor and has all the functionality Unltraedit has and more. BUT: you need to customise it to suit your needs. Here is an address to get you started:
[http://www.micahcarrick.com/09-29-2007/gedit-html-editor.html]("http://www.micahcarrick.com/09-29-2007/gedit-html-editor.html")

Don't know about the converter, somebody else will have to jump in.

---

### Post by esafwan on 2008-10-30
We have good replacement for ultra edit.
[COLOR="DarkOliveGreen"]NOTEPAD++[/COLOR] - Get it [here]("http://notepad-plus.sourceforge.net/uk/nppLinux.php"). [COLOR="Red"]Use this with Gedit and UltraEdit is past!
[/COLOR]

Features:

Here are the features of Notepad++ :
	1.[COLOR="Red"]**Syntax Highlighting and Syntax Folding**[/COLOR]
	
[COLOR="Red"]**2.Supported languages :**[/COLOR]
> C	C++	Java	C#	XML	HTML
PHP	CSS	makefile	ASCII art (.nfo)	doxygen	ini file
batch file	Javascript	ASP	VB/VBS	SQL	Objective-C
RC resource file	Pascal	Perl	Python	Lua	TeX
TCL	Assembler	Ruby	Lisp	Scheme	Properties
Diff	Smalltalk	Postscript	VHDL	Ada	Caml
AutoIt	KiXtart	Matlab	Verilog	Haskell	InnoSetup
CMake	YAML
	
WYSIWYG
	
3.[COLOR="Red"]**If you have a colour printer, print your source code (or whatever you want) in colour.**[/COLOR]
	
4.[COLOR="Red"]**User Defined Syntax Highlighting**[/COLOR]
	
> It allows user to define his own language : not only the syntax highlighting keywords, but also the syntax folding keywords, comment keywords and the operators.
	
5.[COLOR="Red"]**Auto-completion**[/COLOR]
	
> For most supported languages, user can make his/her own API list (or download the api files from dowload section). Once the api file is ready, type Ctrl+Space to launch this action .For more information about Auto-completion, please see Auto-completion HOWTO.
	
6.[COLOR="Red"]**Multi-Document**[/COLOR]
	
> You can edit several documents at the same time.

7.[COLOR="Red"]**Multi-View**[/COLOR]
	
> You have two views at same time. That means you can visualize (edit) 2 different documents at the same time. You can visualize (edit) in the 2 views one document at 2 different positions as well. The modification of document in one view will carry out in another view (i.e. you modify the SAME document when you are in clone mode).

8.[COLOR="Red"]**Regular Expression Search/Replace supported**[/COLOR]
	
> You can search and replace one string in the document by using the regular expression.
	
9.[COLOR="Red"]**Full Drag &#8216;N' Drop supported**[/COLOR]
	
> You can open a document by drag & drop. You can also move your document from a position (or even a view) to another by drag & drop.
	
10.[COLOR="Red"]**Dynamic position of Views**[/COLOR]
	
> The user can set the position of the views dynamically (only in 2 views mode : the splitter can be set in horizontal or in vertical)
	
11.[COLOR="Red"]**File Status Auto-detection**[/COLOR]
	
> If you modify or delete a file which opened in Notepad++, you will be notified to update your document (reload the file or remove the file).
	
12.[COLOR="Red"]**Zoom in and zoom out**[/COLOR]
	

13.[COLOR="Red"]**Multi-Language environment supported**[/COLOR]

	
14.[COLOR="Red"]**Bookmark**[/COLOR]
	
> User can just click on the bookmark margin (located right side of line number margin) or type Ctrl+F2 to toggle a book mark. To reach the bookmark, type just F2 (Next bookmark) or Shift+F2 (Previous bookmark). To clear all bookmarks, click the Menu Search->Clear All bookmarks.
	
15.[COLOR="Red"]**Brace and Indent guideline Highlighting**[/COLOR]
	
> When the caret stay beside of one of those symbol { } [ ] ( ) , the symbol beside of caret and its symmetric opposite symbol will be highlighted, as well as the indent guideline (if any) in order to locate the block more easily. 
	
16.[COLOR="Red"]**Macro recording and playback**[/COLOR]
	
> You can save several macros and edit their keyboard shorcuts for the next use. 


And the most interesting this is that it support plugins and has 100's of them.
 
And one last thing, please post back about your experience. I'm afraid that i have not used it in linux so far. But I have used in windows for long. I'm using Gedit under linux!
__________________________________________________

NOTEPAD++ - Get it [here]("http://notepad-plus.sourceforge.net/uk/nppLinux.php").

---

### Post by scizzo on 2008-10-30
My suggestion would be to use Vim and GVim. However Gedit, Geany are good also.

GIMP for editing images and Inkscape for SVG images.

---

### Post by timcredible on 2008-10-30
photoshop:  digikam + kipi-plugins + gimp + rawtherapee will replace photoshop.  there is a good book out on learning gimp, if that would help.  if the issue is just that you don't want to learn anything new, can't help you there.

video editing:  ffmpeg + winff (gui for ffmpeg) will convert anything to anything, including flv and mp3.

---

### Post by esafwan on 2008-10-30
And here is the final solution!

Alternate 4 Total Media Convertor:

Actually u hav to use a set of app.

1.[COLOR="Red"]**DVD - Mpeg**[/COLOR]: Get it [here.]("http://handbrake.fr/?article=details")
HandBrake is an open-source, GPL-licensed, multiplatform, multithreaded DVD to MPEG-4 converter, available for MacOS X, Linux and Windows.

> Supported sources:

    * Any DVD-like source: VIDEO_TS folder, DVD image or real DVD (encrypted or unencrypted, but protection methods other than CSS are not supported and must be handled externally with third-party software), and some .VOB and .TS files
    * PAL or NTSC
    * AC-3, DTS, LPCM or MPEG audio tracks

Outputs:

    * File format: MP4, MKV, AVI or OGM
    * Video: MPEG-4 or H.264 (1 or 2 passes or constant quantizer/rate encoding)
    * Audio: AAC, MP3, Vorbis or AC-3 pass-through (supports encoding of several audio tracks)

Misc features:

    * Chapter selection
    * Basic subtitle support (burned into the picture)
    * Integrated bitrate calculator
    * Picture deinterlacing, cropping and scaling
    * Grayscale encoding


2.[COLOR="Red"]**Video Converter:**[/COLOR]. Get it [here]("http://www.thugsatbay.com/tab/?q=tab-video-converter-encoder")

> t@b media converter is an audio and video converter / encoder utility which provides a graphical front end for Mencoder*, Sox* and potentially other non-t@b software like RealProducer*.

This utility will convert a great variety (see below) of video and audio formats into files which both zs3 and ZS4 can read/import.

It thus will convert most *.mov *.mpg and similar formats to either AVI/mjpg (for zs4) or to AVI/uncompressed for both zs3 and ZS4.
It can also encode the output of ZS4 into *.mpg files.


> Compatible file formats:

[COLOR="Red"]**Video Input:	**[/COLOR]
avi (mjpg, i420, DV, mpeg4 etc.)
mov (quicktime)
.dv
mpeg/mpg (mpeg1, mpeg2, mpeg4)
3gp (nokia etc.)
mp4
wmv (windows media formats)
rm (real media - only on Linux)

[COLOR="Red"]**Video Output:**[/COLOR]
mjpeg avi (for ZS4 import)
i420 uncompressed avi (both ZS's)
iyuv uncompressed avi ""
mpeg1 (vcd format)
mpeg2
mpeg4
real media (if real producer found on system)

[COLOR="Red"]**Audio Input:**[/COLOR]
wav
mp3
ogg
au
snd
voc
vox
prc
sf
sph
smp
txw

[COLOR="Red"]**Audio Output:**[/COLOR]
wav
ogg
au
snd
voc
vox
prc
sf
sph
smp
txw


3.A Command line way using FFMPEG:

Below is a extract from the site: [http://www.smorgasbord.net](http://www.smorgasbord.net) 
the actual content is [here]("http://www.smorgasbord.net/converting-video-in-linux-using-ffmpeg-and-mencoder/").

> [SIZE="1"]I now have 3 options for converting video well for use in a dvd player in Ubuntu Linux (or any linux distro). If you want to convert video for play on your computer - jump to the end of the article. First I’ll go over the first two which are ffmpeg and mencoder. I used to almost exclusively use ffmpeg when making video to play in a dvd player. I’ve tried both, and gotten very poor quality video and results from mencoder. I know many swear by it, but maybe it needs more resources than my 1.2 Ghz 512MB ram machine will lend. ffmpeg works very well on my older hardware.

On the command line in terminal, you can of course just run the command “man ffmpeg” or “man mencoder” to read the manual (help) page for each to find out how to use them. If you don’t have either on your machine, just install using of course Synaptic Package Manager under System -> Administration. Using the manual pages, I wrote myself some examples that I thought I would most commonly use, and here they are:

FFMPEG on the command line:
===================

by selecting a format as one of the options (”vcd”, “svcd”, “dvd”, “dv”, “pal-vcd”, “ntsc-svcd”, all the format options (bitrate, codecs, buffer sizes) are then set automatically.

You can just type:
$ ffmpeg -i myfile.avi -target vcd /tmp/vcd.mpg

#same example but use high quality, ntsc vcd format
$ ffmpeg -i myfile.avi -hq -target ntsc-vcd /tmp/vcd.mpg

#same example but dvd quality
$ ffmpeg -i myfile.avi -target ntsc-dvd /tmp/dvd.mpg

#same example use same quality as source
$ ffmpeg -1 myfile.avi -sameq -target vcd /tmp/vcd.mpg

#converting a file for VCD format using a and b frames for MPEG 2
$ ffmpeg -i myfile.avi -target ntsc-vcd -bf 2 /home/user/Video/vcd.mpg

#same conversion, but start at 0 seconds and convert only first 45 minutes
#use -ss for start position and -t for duration
$ ffmpeg -i myfile.avi -target ntsc-vcd -bf 2 -ss 00:00:00 -t 00:45:00 /home/user/Video/vcd.mpg

#converting a file to mpeg using mencoder (poorer quality than ffmpeg I think, but that’s on my system - and it really depends on the file and the codec you’re using)
#see the tovid examples below for better better results with mencoder
$ mencoder -oac copy -ovc lavc -of mpeg -o output_file.mpg your_file.wmv

A new trick that I learned was that you can use ffmpeg to extract audio only from video files. Recently I made some .mpg files for a promo dvd I was making for my band. I wanted to also make a promo cd - but use the audio from the video files. Using ffmpeg, it’s possible to rip the audio from any video file (it can convert) directly to an mp3 file like this:
$ ffmpeg -i video.mpg -f mp3 audio_track.mp3

In that example, video.mp3 is your input file and audio_track.mp3 is your output mp3 file. It works great!

I keep a mencoder example around just in case I want or need to try it again and so I have a second option just in case ffmpeg doesn’t work well on a particular video. I sometimes use it to convert windows media files. One last tip - if you are going to be converting any windows media files - you must get the proper codecs installed on your system or ffmpeg won’t work. The easiest way to do this is by running the “Automatix” script explained in the ‘First Things to Do’ section of this guide. It installs the “essential-codecs” from the mplayer site automatically. If you have any problems with this, or don’t want or plan to use Automatix - just download and install them essential codecs from the mplayer web site yourself.

I love using ffmpeg - but some Windows media files it just won’t convert. It will convert a MB or two and then bomb out with a “segmentation fault”. If that happens - I used to try the mencoder option instead. Which brings me to my third and newest option - Tovid. I have found that using the Tovid option gives the best results, and every single Windows media format whether asf or wmv I’ve tried it has converted. Tovid is merely a frontend that uses ffmpeg, mencoder, transcode, and dvdauthor - but it does so very efficiently. I originally installed Tovid on Ubuntu using Synaptic package manager, which made an icon under the Sounds and Video system menu that brings up the 0.22 GUI interface. If you don’t have an icon in that menu, try running “tovidgui” from the command line to bring up the gui. This interface has never worked for me in Breezy (but does in Dapper flight 6). I downloaded the 0.25 Tovid from their web site and installed it from code using their instructions and the Tovid command line tools seem to be working for me so far. If you have any problems with python depencies when you install Tovid - be sure to run these 2 commands on your terminal, and then install Tovid again for it to work right:

$ sudo apt-get install python-wxgtk2.4
$ sudo apt-get install python-dev

Tovid is a suite of scripts that you can use for the various stages of the conversion and burn to disc process. They heavily use mencoder for conversion, and for some reason they do it much better than when I run mencoder myself. The first script of the Tovid suite that you’ll find handy is “idvid” (short for id video). Use it like this:
$ idvid file.avi

It will not only give you the video properties, you will get the width and height, aspect ratio, duration, bitrates, but the most important is the last bits of info you get. It will tell you whether the video and audio is compliant with VCD, SVCD, or DVD. Then you’ll know whether you need to convert it, or if you can burn it straight to disc.

After you run the idvid command on your video(s), you’ll probably need to convert them to the proper mpeg (mpg) format before burning. This is very easy using tovid on the command line. There are a multitude of options you can find in the man page, but these are the two most common I use:

$ tovid -dvd -ntsc file.mpg video
$ tovid -vcd -ntsc file.mpg video

after the tovid command the first option I use is to tell it whether or not to make the video format for a dvd or for a vcd. Then I use the ntsc option for my type of tv. Next I tell it what the input file is. Last, I tell it what to name the output file (prefix only with no extension)…i.e., if you make this video like I did, your output converted file will be video.mpg. If you accidentally name your output file video.mpg, not to worry - tovid will save it as video.mpg.mpg.

If you want to convert lots and lots of videos at once (like I sometimes do), and don’t want to run this command a ton of times, or write a script to convert them - tovid has a nice option. Just use tovid-batch instead like this:

$ tovid-batch -dvd -ntsc -infiles *.avi

You can also convert every single (video) file in a folder like this:
$ tovid-batch -vcd -ntsc -infiles *.*

If you’re not familiar with the command line or dos, the asterik means “do everything like this” (avi). So of course *.mpg would mean all mpg files, *.wmv, all windows media files, *.* means all files of all extensions, etc.

I don’t use it much anymore now that I know about the tovid-batch command, but you can install and using the ‘video-convert’ scripts from the ubuntu forums designed for nautilus. Nautilus is like the dekstop manager is Gnome, and if you right click the desktop - you’ll see a heading entitled “scripts”. Download the video-covert script from the forum and follow the instructions for installing it (it’s very easy). Once installed, just right click any video file(s), go to “scripts -> video-convert” and answer the simple option prompts and voila! It converts them all (using command line tools) for you! The greatest benefit of this is that you can shift-click multiple files at once, and use the script to convert them all one by one. Doing it yourself in terminal you would have to either convert them one by one, or write a script to create them in succession.

If you install this script and like it, you can also visit the ubuntu forums and get the audio-convert script too, to convert audio files the same way. You’ll be converting flac, ogg, wav, and mp3 files in no time. Just make sure that you’ve installed the command line tools for the formats you’ll be converting in synaptic. i.e., if you want to convert .flac files to mp3 using audio-convert, make sure you install the .flac command line tools in synaptic first so the .flac format will be supported and usable by audio-convert.[/SIZE]

_________________________________

Some other place where u get more knowledge:
1.Another Tool (KDE) [here]("http://linux.softpedia.com/get/Multimedia/Audio/Kde-media-converter-27280.shtml").

2.Another cool tool a GUI of FFMPEG [here]("http://linux.softpedia.com/get/Multimedia/Video/Multimedia-Converter-23546.shtml").

3.Another for GNOME [here.]("http://gmencoder.sourceforge.net/")

[COLOR="Red"]Everything is Solved i guess.[/COLOR]:lolflag:

[COLOR="YellowGreen"][COLOR="DarkOliveGreen"][SIZE="5"]One last word, i have not used any of the above software, i just researched on the web just for you! And i have shortlisted the best one out there! Hope you will post back the experience!
[/SIZE][/COLOR][/COLOR]

---

### Post by small_sammy on 2008-10-30
About Photoshop,

I am able to run Photoshop CS2 under Wine with no problems.

---

