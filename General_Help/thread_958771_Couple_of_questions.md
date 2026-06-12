---
title: "Couple of questions"
date: 2008-10-25
forum: General Help
---

### Post by Tanith12 on 2008-10-25
So ive been using Ubuntu now for about a week and am loving it (got the desktop cube goin, pretty awesome for when im in class haha), and i have a couple of questions, whenever i boot up it says Bios Bug 81, im just wondering what that is (my Ubuntu its installed inside of windows vista).  As well are there any good organizational programs, im a University student and a to do list that beeps or makes a sound would be ideal but lacking that i can just keep using the Tomboy notes program.  Also my firefox has been refusing to start up sometimes and am wondering which other browser you suggest for linux, ive looked at a couple like opera and konquerer but i am not sure which to take.  Next lastly how come when im listening to music, my skype will not work? I cannot make calls at all, and when my skype is up my music player will not work.  Lastly when uninstalling a program (Amarok) do i just unselect it and then it will uninstall or is there more to it??

Thanks

---

### Post by ragtag on 2008-10-25
I´ll give a shot at answering some of these (I don´t know the answer to all). :)

Evolution has a calendar and todo list, as well as mail. Events here will show up in the notification area in the panel in Gnome.

When Firefox doesn't want to start, it may have a hung process you need to kill first. There is a processor use indicator you can add to the panel, and you can doubleclick it to see if a firefox is running (like taskmanager on windows).  ps x | grep firefox on the command line will do it too. Aside from that, I kind of like Opera. It's fast and easy to use.

For the Skype problem, search these forums for PulseAudio and how to get it working with different applications.

To uninstall a package in Synaptic Package Manager, right click it and choos Mark for Removal, then hit apply. It should list the packages that will be removed. Note that some packages take with them stuff, you really don't want to remove.

Hope that helps.

---

