---
title: "dailystrips help"
date: 2008-11-03
forum: General Help
---

### Post by hfw on 2008-11-03
I am hoping there are some dailystrips users out there who can help me.  As far as I can tell there is no current development to this program.  

I've been using dailystrips for a while to download comics for my wife and I to read.  I looks as if united media has changed the setup of their pages, and the comics from there are no longer downloading.  I tried going to comics.com, which is the site for their comics now, but am unable to figure out how to set up the class in my strips.def file to download from there.

Thanks in advance,
Hal

---

### Post by k_dog on 2008-11-04
Hal,
I just got my script working again today. All you need to do is replace "unitedmedia" with "comiczone" under the class and it should work again.

-kdog

---

### Post by hfw on 2008-11-04
I'll give it a shot.  If it works, you're a genius.  I tried comics.com, and it failed miserably...

Thanks in advance.  (My wife will thank you as well)

-hal

edit:

Thank You! Thank You! Thank You! Thank You! Thank You! Thank You! Thank You!

---

### Post by k_dog on 2008-11-19
Hal,
Many of the united media comics stopped working for me last week. The trick that I used to fix the problem (simply switching the server used) no longer functioned because they stopped updating that server for daily comic content.

So I took an hour or so today to look at how to fix this. All content is now thru comics.com instead of unitedmedia.com/comiczone.com and the directories containing the images have changed. Three changes will be needed to get this working again:

1) Change the class for unitedmedia to
class unitedmedia-srch-comics
        homepage http://www.comics.com/$strip/
	type search
        searchpage http://comics.com/$strip/%Y-%m-%d/index.html
	searchpattern <img.+?src="(http://assets.comics.com/dyn/str_strip/.+?)"
        baseurl 
	provides any
end

2) Any strips with more than 1 word in its name must change its strip definition to show the whole strip name, with each word separated by an underscore. 
e.g.  "strip getfuzzy" would become "strip get_fuzzy"
or    "strip alleyoop" would become "strip alley_oop"

3) Dilbert is an oddball (there may be others but this was the only one I encountered). Dilbert needs to use the same class as before. So I just created a new class just for it. It's strip definition should be updated to point to this class. Below is the class:
class unitedmedia-srch-comics-dilbert
        homepage http://www.comiczone.com/comics/$strip/
        type search
        searchpage http://www.comiczone.com/comics/$strip/archive/$strip-%Y%m%d.html
        searchpattern <img.+?src="(/comics/$strip/archive/images/$strip.+?)"
        baseurl [http://www.comiczone.com](http://www.comiczone.com)
        provides any
end


I think this will get everything back working for unitedmedia comics. Let me know if you have any questions.

---

### Post by hfw on 2008-11-20
kdog,

Great work.  Thanks a bunch.  I worked on this yesterday as well, but had not gotten the searchpattern line correct.  

Do you have anything from Gocomics.com that you fetch?  I have some from there that I want to try and work on.  Here is my first attempt for foxtrot classics which seems to work.  The only thing I saw that was odd is that the abbreviation for the strip that they use in the filename is different than what they use for the homepage url.


class gocomics-gen
	homepage http://gocomics.com/$strip
	type generate
	imageurl http://picayune.uclick.com/comics/$strip/%Y/$strip%y%m%d.gif
	provides any
end


strip ftcl
	name Foxtrot Classics
	homepage [http://gocomics.com/foxtrotclassics](http://gocomics.com/foxtrotclassics)
	useclass gocomics-gen
end

---

### Post by k_dog on 2008-11-20
Yep, I use a few gocomics strips (but not foxtrot classics). I don't believe you need to rename the strip if you don't want. You should be able to take care of this by passing the name through using the $1 var. That is, do something like:

strip foxtrot_classics
        name Foxtrot Classics
        homepage [http://gocomics.com/foxtrotclassics](http://gocomics.com/foxtrotclassics)
        useclass gocomics-uclick-gen
        $1 ftcl
end

This has usually worked for me. :-)
-k_dog

---

### Post by hfw on 2008-11-20
Thanks for the suggestion.  That is a much cleaner look.  

-hal

---

