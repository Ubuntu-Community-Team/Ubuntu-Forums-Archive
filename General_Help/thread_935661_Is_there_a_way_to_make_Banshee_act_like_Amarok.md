---
title: "Is there a way to make Banshee act like Amarok"
date: 2008-10-01
forum: General Help
---

### Post by Excalibre on 2008-10-01
Subtitle: Is it possible to find a free software music player that doesn't ******* suck?

Seriously. Is this such a weird use case? "User owns music and occasionally likes to listen to it. User likes to play the music he is in the mood for at the moment. User sometimes is not listening to music, so it is unnecessary for music to play 24 hours a day."

I'm somewhere between enraged and just completely ******* puzzled at the moment, after just having tried Banshee for the first time. I was shocked that there was another music player with the same godawful usability as Rhythmbox -- what, one unforgivably terrible music player wasn't enough? We need two?

The basic problem with these two pieces of software is that there is no support for what is the default music listening behavior, judging by EVERY music player in the non FOSS world, and the behavior of every human being I've ever met. Which is this: someone wants to listen to some music. So he queues up some stuff to listen to. Maybe individual songs, maybe albums, whatever. Then when the queue runs out the music stops. Basic, basic behavior, right? This is the normal way to use Amarok and Exaile, not to mention other kinds of media players like Totem or Mplayer, and not to mention every piece of media software in the FOSS world. I'm amazed that this absolutely basic functionality is missing on not one but TWO otherwise usable pieces full-featured music management software, Rhythmbox and Banshee, and unfortunately they're the only ones like it for Gnome.

I could just continue to use Amarok, but I really don't like having all that KDE infrastructure running when I'm not using KDE, and it doesn't run very well or stably on Gnome. Exaile works in the same basic way and eventually it'll probably be quite a good piece of software, if the developer continues, but it's just too buggy right now for me to want to use it. It's astonishing -- and more than a little appalling, frankly -- that the Gnome desktop has nothing that's even vaguely equivalent to Amarok in providing normal media player functionality. It's great to have support for radio, and podcasts, and playlists (both dumb and smart) -- these are all cool things but the most basic use case is just not supported on Rhythmbox and Banshee and it really shocks me that apparently other people are willing to put up with this.

If I just click something in my library, I have no ability to create a queue -- I can choose an album, or a song, or whatever, but as soon as it's done it goes on to the next thing, and that often means going to the next artist in alphabetical order (because, having listened to one artist whose name starts with P, undoubtedly I'm in the mood for others that also start with P, right? Yeah, doesn't exactly make sense.) It doesn't ******* stop. Why doesn't it stop? I told it what I wanted to listen to, then I listened to it. Isn't it supposed to be up to me what music I listen to, and when? Why is this software so hostile to the basic idea that I should be able to listen to music sometimes and not listen to music other times?

The play queue almost sort of does what I want, except songs disappear right after playing, which is irritating, and it defeats the purpose of the play queue anyway (which is really quite an ingenious concept -- I'm often listening to one album but get the sudden urge to listen to some other song before going back to what I was listening to.)

Banshee would be a really awesome piece of software because of all the other stuff it does, but it's totally unsuited to the basic way of listening to the music because of all this. I don't usually want to bother with playlists, or queue up my entire library on shuffle, or something. This is something that could be implemented with an extension, probably, but I have no ******* clue where to begin doing something like that.

I don't know why I'm even bothering to ask, but does anyone know of a decent non-KDE music player? One that supports the basic functionality of _listening to music_? I don't want to have to pick each album I want to listen to it as the previous one ends. Playlists suck because you can't actually order things on them -- they can be ordered alphabetically by artist, or album, or whatever, but they won't retain the order the user chooses. Besides, I don't want to have to create playlists. It's more work. I don't want to have to hit the stop button[SIZE="1"]*[/SIZE] every time I want to stop listening to music -- if there's nothing queued up, why is the software trying to force me to listen to something? I'm capable of making decisions of that magnitude all on my own, honest.

[SIZE="1"]*Said for effect, as there's NO ******* STOP BUTTON. Seriously, what the ****? I'm not allowed to start a song over at the beginning when I get interrupted? The software needs to retain its position -- which is probably two seconds into the song that _it started playing without my ******* permission_?! How the **** can BOTH major Gnome music players be broken in exactly the same way? Is this the Gnome way of listening to music -- the user obeys the software, rather than vice versa?[/SIZE]

All this **** about "freedom" and "choice" may apply in some abstract sense but I'm sick of ******* using Ubuntu on the desktop because I'm sick of every ******* application out there deciding for me what I'm allowed to do, either by simply not supporting normal things that non-free equivalents all do, or by -- like here -- trying to force the user into some shitty ******* idea the developer had about how people SHOULD listen to music.

I know this is really just another case of shitty application design and I should probably get used to it if I'm going to keep using Linux, but is this really going to help the FOSS community attract new people? Someone gets Ubuntu (or any other distro), tries it out, and discovers it _won't let them_ play their music the normal way? I know it's crappy software, but the natural feeling here for users is that they're not permitted to listen to their music -- they have to try to figure out ways to convince a bad application to maybe sort of allow them to listen to what they want to. This is REALLY BAD. This is the sort of thing that makes people angry! It makes them NOT WANT TO USE UBUNTU. It makes them NOT WANT TO USE LINUX. Groups like Ubuntu and Gnome need to FIX THIS. There's always going to be shitty software but they need to not be shoving the worst of it onto users by default, and they need to figure out ways to promote development of promising but still unfinished software like Exaile.

Sorry. I had to get this off my chest. I'm feeling a lot of FOSS angst right now. If anyone knows of a decent music player, it would help a lot.

---

### Post by mc4man on 2008-10-02
While personally i only use Amarok, I'm certainly not going to suggest you use it (not after above) I'm mentioning only because *audacious* also has most of the same capabilities for 'non standard' use that you may or may not find useful. (Audacious's commands are worded a little different.

possibly you may find some added control 

For my own use I never made a playlist, collection and hardly ever see Amarok's gui. Basically music is stored in a directory with sub and sub/sub directories, mainly as artist - albums, with some mixes and loose tracks, folders scattered around the desktop.

Control is based on three command parameters - load, queue, and append, any of which can also take a play parameter. I find '--load --play' the best use of play.

Load - loads what's been selected while removing current playlist if any, begins immediate playback when combined with 'play'
Queue - adds what's been selected directly below current playing track.
Append - appends what's been selected to end of current list.

Any or all of these can be used in a multitude of ways.

Right click nautilus actions, used on anything from single files to folders including sub folders if wished.( playback order determined by order listed or numbered.

Made into  custom file associations for d. left clicking on single files.

You can also add part or all of your collection to the right click menu allowing for immediate access and playback by simply r .clicking on the desktop or in a file browser and clicking on the listing you wish to hear. 

nautilus actions (audacious in post 8, file associations based on these also

[http://ubuntuforums.org/showthread.php?p=5287915#post5287915](http://ubuntuforums.org/showthread.php?p=5287915#post5287915)

adding collection to r. click menu (scripts

[http://ubuntuforums.org/showthread.php?t=921208](http://ubuntuforums.org/showthread.php?t=921208)

---

### Post by amac777 on 2008-10-02
I realize you probably just wanted to rant to release some stress, but I use rhythmbox and it seems pretty easy to do what you want. So I figured I'd respond on the off chance that it helps.

Regarding the music never stopping when it finishes the end of a playlist or the queued music, make sure the "Repeat" button at the top is not pressed and then it will stop when it finishes playing the list of songs.

Regarding making a queued list that won't get changed (erased) as you play through the songs on the list, use playlists instead. I know you said you don't want to, but I don't understand why not? Making a playlist is just as easy as making a queued list - just right click on the song and say add to playlist instead of add to play queue. Think of playlists as permanent lists, whereas the play queue is a temporary interrupt and takes preference over whatever list is currently playing.

Regarding making the songs on either the play queue or a playlist play in the order you want, make sure the "Shuffle" button at the top is not pressed and then they will play in the order you specify. Note that you can drag and drop the songs within both the play queue (temporary) or any playlist (permanent) to change the play order at any time. You said this doesn't work and that you can only order by artist or other categories but your mistaken. Just drag and drop the songs within the playlist in whatever order you want and it will remember the new order.

Regarding there being no stop button, I'm not 100% what you wanted from your comments. If you want to not restart the song you can just click (uncheck) the play button at the top to pause at any time. It works just like pause and you can resume the music by pressing the play button again whenever you want. On the other hand, if  what you wanted is to restart the song at the beginning, you can just double click the song in the playlist (it's highlighted in orange so easy to see). 

I think I addressed all the specific questions you asked, but it was a long rambling post so I might have missed some. Anyway, hope you're feeling better by the time you read this. Have a good one.

---

### Post by Excalibre on 2008-10-02
> **amac777 said:**
> Regarding the music never stopping when it finishes the end of a playlist or the queued music, make sure the "Repeat" button at the top is not pressed and then it will stop when it finishes playing the list of songs.
You're right about this, Rhythmbox does indeed stop when a playlist is done (unlike Banshee.) So that's at least better.


> Regarding making a queued list that won't get changed (erased) as you play through the songs on the list, use playlists instead. I know you said you don't want to, but I don't understand why not? Making a playlist is just as easy as making a queued list - just right click on the song and say add to playlist instead of add to play queue. Think of playlists as permanent lists, whereas the play queue is a temporary interrupt and takes preference over whatever list is currently playing.
Right. The problem for me is it's still way harder than just double clicking, which is all I have to do in Amarok. I have to instead drag it over to a playlist (more error prone) or use some right-click menu (more work) because it can't just have an automatic "playlist for right now" functionality out of the box or at very least available in the preferences.


> Regarding making the songs on either the play queue or a playlist play in the order you want, make sure the "Shuffle" button at the top is not pressed and then they will play in the order you specify. Note that you can drag and drop the songs within both the play queue (temporary) or any playlist (permanent) to change the play order at any time. You said this doesn't work and that you can only order by artist or other categories but your mistaken. Just drag and drop the songs within the playlist in whatever order you want and it will remember the new order.
You're right. It does indeed work this way in Rhythmbox, which means it's (again) marginally less broken than Banshee, which doesn't allow you to order the tracks in a playlist at all (although you can have it sort them alphabetically, or by artist, or by album, or whatever, you can't just put them in the order you want.)


> Regarding there being no stop button, I'm not 100% what you wanted from your comments. If you want to not restart the song you can just click (uncheck) the play button at the top to pause at any time. It works just like pause and you can resume the music by pressing the play button again whenever you want. On the other hand, if  what you wanted is to restart the song at the beginning, you can just double click the song in the playlist (it's highlighted in orange so easy to see).
Right. So if I'm not looking at the particular playlist in question, I have to switch to looking at it (does it let me see my library and the playlist at the same time? I don't remember.) Or they could add a stop button, at a cost of zero (since there's room for it) and with the advantage of providing the same interface items as every other media player out there (except Banshee.) But they don't, and because of what ? Because it's a Gnome application, and the Gnome way is to make sure everything people are used to from other Desktop environments, operating systems, and their own damn CD player is inapplicable? Because we have to take away every ******* bit of functionality people like and expect and are used to, in order to Keep It Simple? Why do I have to do several more clicks to stop a track and restart it at the beginning? Why is this basic functionality taken away, so I have to go through a roundabout process that takes longer and is less convenient to use it? There's some kind of retarded user interface philosophy at work here, which is to take away the user's ability to do anything except what the application's authors want them to do, and this is EXACTLY why Rhythmbox should get kicked out of Gnome, and out of Ubuntu. Applications that are written in a way that makes them unusable and whose authors are [disrespectful of users](http://braid-game.com/news/?p=364) -- both in their actual speech and the way they design their software -- shouldn't be welcomed into desktops and distributions. Siccing these people on your users is counterproductive!


> I think I addressed all the specific questions you asked, but it was a long rambling post so I might have missed some. Anyway, hope you're feeling better by the time you read this. Have a good one.
Thank you. And yeah, I can basically get it to do mostly the same things as Amarok except every step of the way is a ton of extra work. I can't just sort of go through my music and find some stuff I want to listen to, not in the same way, because it's three times the effort -- and hard to figure out to boot. Why does it have to be this way? I'm fine with working to figure out how to use some sophisticated application that does sophisticated things. I have no problem with the fact that spreadsheet apps, or databases, or image editors have a learning curve because if you're going to do something complicated you're going to have to do some work along the way. I don't WANT to have to figure out a music playing app, though, and I don't want it to be a lot of work to use it, and I don't get why there only seems to be one FOSS app whose authors get that.

So I'm back to Amarok, which really is an excellent application (though of course it has some bugs and rough edges.) I don't get why I don't have a similar choice that's native to my desktop environment, though. Especially because I hate that KDE look.

---

