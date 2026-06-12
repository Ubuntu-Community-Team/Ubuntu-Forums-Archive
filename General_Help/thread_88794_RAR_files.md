---
title: "RAR files"
date: 2005-11-11
forum: General Help
---

### Post by Ocxic on 2005-11-11
I recently downloaded a file zipped into .rar files, plit up into about 30 seperate peices, and I am unabel to extract it, is there a way to re-combine all the rar files to one, or is there a prog i could download?

---

### Post by voth on 2005-11-11
Look in Synaptic for unrar install, then open a terminal and type unrar /? for the commands.

If I'm reading your post correctly that is.

---

### Post by stfu on 2005-11-11
[QUOTE=Ocxic]I recently downloaded a file zipped into .rar files, plit up into about 30 seperate peices, and I am unabel to extract it, is there a way to re-combine all the rar files to one, or is there a prog i could download?[/QUOTE]
After installing rar I've been able to extract split volumes in nautilus with right click and extract here (it extracts files from all archives). Not quite sure about password protected archives, but you could always use GnomeRAR to extract them. It supports also password protected archives.

---

### Post by Ocxic on 2005-11-11
i tried what you sadi but it still isn't working...???

---

### Post by drogoh on 2005-11-11
[QUOTE=Ocxic]I recently downloaded a file zipped into .rar files, plit up into about 30 seperate peices, and I am unabel to extract it, is there a way to re-combine all the rar files to one, or is there a prog i could download?[/QUOTE]

You only need to extract the first one.  RAR is intelligent enough it will unpack from all of the others (provided you aren't missing any).

Edit:  I suppose I should provide a viable solution.  Since I don't know of a GUI to do it off hand, since I'm using Windows right now and not Ubuntu, install 'rar' from Synaptic, open a terminal and do this:

```

cd /path/to/files
rar e file.rar

```

Or somewhere thereabouts.  I'm pretty sure that will work, even though I'm playing off memory.

---

