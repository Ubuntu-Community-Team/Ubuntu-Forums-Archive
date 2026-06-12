---
title: "File Browser search hidden files/folders (8.10)"
date: 2008-11-01
forum: General Help
---

### Post by Jim Danner on 2008-11-01
**Note**: I am aware of the existence of command line tools like *locate* and *find*. This question is specifically about the built-in GUI search in Nautilus File Browser.

When I search with gnome-search-tool (Places... Search), I am able to find hidden files (like ~/.gtk-bookmarks when I search for *book*) and files that are in hidden folders (like ~/.config/user-dirs.locale when I search for *dirs*). This is done by selecting Additional options and adding "Show hidden and backup files." as an option. Using the Configuration editor, I even managed to make this the default behavior (checking the boxes at /apps/gnome-search-tool/select/show_hidden_files_and_folders and /apps/gnome-search-tool/show_additional_options).

However, when I'm searching inside the Nautilus file browser, I can't do this. The Additional options do not include "Show hidden files". Of course I have "Show hidden and backup files" selected in the File Manager preferences, but it doesn't help.

Often the built-in Nautilus search is the quickest and nearest option for searching, but it has this serious problem. Can this be changed?

---

### Post by adieb on 2008-11-01
Mmmh, i thought it would change nautilus search behaviour when you switch to "show hidden files" mode.

But I just figured out, that it doens´t.

Hope you find the solution and post it here...

---

### Post by Jim Danner on 2008-11-02
> **adieb said:**
> Hope you find the solution and post it here...Not found any solution on the internet yet. This blogger suggests there should be an integrated search function in Ubuntu: [http://brainstorm.ubuntu.com/idea/14598/](http://brainstorm.ubuntu.com/idea/14598/) . That makes a lot of sense, but it doesn't exist apparently, and every application has its own search particulars.

As far as I have seen, Nautilus has been built with a deliberate choice to disable search for hidden files. (Windows-Ubuntu 1-0)

---

### Post by sklyer on 2008-12-17
You can see hidden files in Nautilus by typing Ctrl-h in the directory where you suspect there are hidden files.

---

### Post by Jim Danner on 2008-12-21
> **sklyer said:**
> You can see hidden files in Nautilus by typing Ctrl-h in the directory where you suspect there are hidden files.Yes, we all know that, but it has nothing to do with the problem described here. If we already "suspect" a file to be in a certain place, we don't need a search function.

---

### Post by thunderbirdje on 2009-01-10
There is a panel applet called "Deskbar" which is able to search for files (and other stuff like through bookmarks) but I don't know if also search hidden files?

I'm also missing a kind of more extended search functionallity in nautilus :( -or is there and am I not aware of it? -

---

### Post by mdurham on 2009-01-10
Jim Danner, It is possible to do this because I set-up 'find' in Nautilus to do exactly what you want. It always scans hidden folders/files. The problem is I can't remember how I did it. I do have those fields set the same as you in the Configuration editor. I also messed around from within Nautilus, setting the 'find' options there. If you set the options from within Nautilus maybe it will save them as default??? Sorry, I just don't remember.
Anyway I just write this in order to encourage you not to give up, it is possible.
Cheers, Mike

---

### Post by Jim Danner on 2009-01-15
> **mdurham said:**
> Jim Danner, It is possible to do this because I set-up 'find' in Nautilus to do exactly what you want. It always scans hidden folders/files. The problem is I can't remember how I did it. I do have those fields set the same as you in the Configuration editor. I also messed around from within Nautilus, setting the 'find' options there. If you set the options from within Nautilus maybe it will save them as default??? Sorry, I just don't remember.
Anyway I just write this in order to encourage you not to give up, it is possible.
Cheers, MikeI guess that would mean you hand-edited some of Nautilus's configuration files (since I nor anyone else had found any relevant "official" configuration elements, like Edit... Preferences or the Ubuntu Configuration Editor). It's a pity you don't remember, but do you remember/know by any chance what are the configuration files that Nautilus has? I might take a look inside...

EDIT: Or perhaps you managed to use the gnome-search-tool as a plugin in Nautilus?

---

### Post by mdurham on 2009-01-15
> **Jim Danner said:**
> I guess that would mean you hand-edited some of Nautilus's configuration files (since I nor anyone else had found any relevant "official" configuration elements, like Edit... Preferences or the Ubuntu Configuration Editor). It's a pity you don't remember, but do you remember/know by any chance what are the configuration files that Nautilus has? I might take a look inside...

EDIT: Or perhaps you managed to use the gnome-search-tool as a plugin in Nautilus?

Sorry Jim Danner, as far as I remember I didn't edit any config files. What I meant was that I ran a search from within Nautilus (I have a right-click to start the search using 'Nautilus actions'->gnome-search-tool) and set it up to search for hidden files there, and maybe it remembers my settings. I do remember having to open option after option until I found 'show hidden and backup files' then closing all the open options above it just to leave 'show hidden and backup files'.
Cheers, Mike

---

### Post by ronewolf on 2009-12-29
> **Jim Danner said:**
> Using the Configuration editor, I even managed to make this the default behavior (checking the boxes at /apps/gnome-search-tool/select/show_hidden_files_and_folders and /apps/gnome-search-tool/show_additional_options).
Thanks for this pointer! At least better than nothing...

> **Jim Danner said:**
> However, when I'm searching inside the Nautilus file browser, I can't do this. The Additional options do not include "Show hidden files". Of course I have "Show hidden and backup files" selected in the File Manager preferences, but it doesn't help.

Often the built-in Nautilus search is the quickest and nearest option for searching, but it has this serious problem. Can this be changed?
Too bad no solutions on this, I agree with y'all that it would be a desirable feature. I've just started learning about Nautilus scripts, maybe a solution there (not sure). Still, inconvenient to have to run scripts...

---

### Post by Eugene_Bondarenko on 2010-01-05
Hi, I am running Ubuntu 9.10 and this feature seems to be present here. However the search must be accessed not via ctrl+F in folder (which brings a search field at the top of the folder). When I accesses it this way, hidden stuff is not included in the search results. But when access it via Applications => Accessories => Search for Files, I get an advanced search window where you can do whatever you want if you go to "Select more options". "Shown hidden and backup files" is there too. I don't have any idea if Ubuntu 8.10 has this, but you can give that a try.

---

### Post by spota on 2010-01-13
Yes, that gets me to the search dialog that allows for selecting "Show hidden and backup files", but nevertheless it does not work.
I'm trying to retrieve all the hidden folders added by subversion (.svn) in a directory tree.

---

### Post by MrKlister on 2010-05-04
These obvious design flaws are the ones that gives me doubts about ubuntu.
This was one of the big things that annoyed me when I switched from windows to ubuntu for two years ago. And it still is not fixed.

---

### Post by Eugene_Bondarenko on 2010-05-04
Uh, well, I am not sure about 8.10 but this feature worked fine for me in 9.10 and continues to work fine in 10.04.

---

### Post by Jim Danner on 2010-05-04
> **Eugene_Bondarenko said:**
> Uh, well, I am not sure about 8.10 but this feature worked fine for me in 9.10 and continues to work fine in 10.04.I've just tried it again, in a freshly installed version of Ubuntu 10.04. Here are the steps:
[LIST=1]
[*]Open a file browser (Places... Home Folder)
[*]Click the magnifying glass or choose Go... Search for Files
[*]Type a search term, e.g. *book*
[/LIST]
I still get nothing, while there are several hidden files (e.g. ~/.gtk-*book*marks) and files in hidden folders (e.g. ~/.gconf/apps/net*book*-launcher).

Maybe you went straight to Places... Search for Files. As you can read in the OP, this thread is about searching from within the file browser (because that is often where you are when you realize you can't find a file and want to do a search).

---

### Post by dFlyer on 2010-05-04
Search function works both from the Places menu on the tool bar and from the Go menu and icon on my File Browser folder in 10.04.

---

### Post by Jim Danner on 2010-05-05
> **dFlyer said:**
> Search function works both from the Places menu on the tool bar and from the Go menu and icon on my File Browser folder in 10.04.That's amazing... does it actually find hidden files like .gtk-bookmarks? What settings did you use?

---

### Post by sebzen on 2010-05-17
On Ubuntu 10.4, I can't find hidden files/folders. 

I just tried to search all ".svn" folders of a given folder (with the "show hidden files and folders" option enbabled) nothing found ...

---

### Post by Jim Danner on 2010-05-17
> **sebzen said:**
> On Ubuntu 10.4, I can't find hidden files/folders. 

I just tried to search all ".svn" folders of a given folder (with the "show hidden files and folders" option enbabled) nothing found ...Yes, same problem here. I have lost hope that the Nautilus developers are going to take this issue up any time soon. But it annoyed me so much that I took the trouble of installing the entire software development environment in Ubuntu, downloading the Nautilus source code, and tracking down the problem -- just to get rid of it.

Turns out that installing the development environment and finding out how to compile the source code was by far the hardest part of that. Making the changes so that hidden files are searched when you have selected *Show hidden and backup files* in Preferences was a matter of adding 4 lines of code in a single file. Literally. No more.

I must say the relief of being able to search hidden files (and files in hidden folders) is greater than I expected. It is really extremely convenient to search right from where you are -- that is, in the file browser.

---

### Post by sebzen on 2010-05-17
> **Jim Danner said:**
> Yes, same problem here. I have lost hope that the Nautilus developers are going to take this issue up any time soon. But it annoyed me so much that I took the trouble of installing the entire software development environment in Ubuntu, downloading the Nautilus source code, and tracking down the problem -- just to get rid of it.

Turns out that installing the development environment and finding out how to compile the source code was by far the hardest part of that. Making the changes so that hidden files are searched when you have selected *Show hidden and backup files* in Preferences was a matter of adding 4 lines of code in a single file. Literally. No more.

I must say the relief of being able to search hidden files (and files in hidden folders) is greater than I expected. It is really extremely convenient to search right from where you are -- that is, in the file browser.


Awesome Jim !! 

You must have been really motivated to checkout everything and make it work :)

Do you plan to submit a patch anytime soon ?
I can't believe it's only 4 lines code. This forum thread is open since 8.10 ...

Thanks again for the hope :)

PS: bug on launchpad : [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/334125](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/334125)

---

### Post by Jim Danner on 2010-05-17
> **sebzen said:**
> Do you plan to submit a patch anytime soon ?

PS: bug on launchpad : [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/334125](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/334125)Oh well, why not... I've submitted it in the official [GNOME bug reporting system]("https://bugzilla.gnome.org/show_bug.cgi?id=437626"). Don't get your hopes up, it's not looking like they care much...

---

### Post by Splat_NJ on 2010-12-01
I'm only about 2 weeks into Linux (running Ubuntu10.10) so go easy on me guys. 

I guess this still hasn't been resolved because I need to manually select the "Select More Options", then select the show hidden and backup files option. I see there is a patch to change the default behaviour but I've no idea how to run it and is it still safe to use with 10.10 and newer? Thanks.

---

### Post by Jim Danner on 2011-01-12
> **Splat_NJ said:**
> I guess this still hasn't been resolved because I need to manually select the "Select More Options", then select the show hidden and backup files option. I see there is a patch to change the default behaviour but I've no idea how to run it and is it still safe to use with 10.10 and newer? Thanks.Indeed, this has not been solved in the Nautilus file browser. But in the place where you are (Places... Search for files), you can make hidden files appear in the results by default. Read the very first post of this thread for more.

---

### Post by jcottier on 2011-06-29
"Places..Search for files" was not finding anything in hidden folders for me, with the "Show hidden and backup files" option on. I know it used to work. So I tried removing the option, then re-added it and voila! it now works again.

---

### Post by Splat_NJ on 2011-06-29
Off the top of my head I can't remember how I did it but I have the hidden files/folders option enabled by default now. Still, it doesn't always find the files or folders searched for, even when they are not hidden.

---

