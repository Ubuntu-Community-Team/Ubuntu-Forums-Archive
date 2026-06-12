---
title: "Associating .torrent with uTorrent in Firefox"
date: 2008-08-26
forum: General Help
---

### Post by jtreach on 2008-08-26
I have used [this]("http://ubuntuforums.org/showpost.php?p=1421017&postcount=11") guide to associate .torrents with utorrent and have also set firefox to use the utorrent.exe as the default handler of .torrent files. However, when I try to open a torrent file utorrent gives me the following message:

> Unable to load "/tmp/TORRENTFILENAME.torrent": Path not found!

Does anybody know how to fix this?

---

### Post by Scunge on 2008-08-26
This isn't exactly answering your question, but might solve it through coincidence.

Sometimes, browsers can get a bit confused about files it has downloaded, and can mess up downloading a torrent file and passing it directly to uTorrent. I don't know exactly **why** this is the case, all I know is that quite often the problem can be worked around by forcing your browser to save the torrent file to disk, and then opening the torrent file manually in uTorrent. It's a little less convenient than just click-and-go on the torrent title, but if it saves some unnecessary fault-finding and tearing out of hair...

So save the torrent file to your desktop for ease of use, and then use the **File > Open** option (whatever it's called) in the menu, pointing it to the torrent file you have saved on your desktop.

Also, it can sometimes be useful to save the torrent files away, in case of moving to another client or computer, or in case case of trackers with a limited torrent lifetime, to reseed the torrent. Having them on the desktop means you can easily find and save them, rather than hoping you can find it in /tmp or wherever it happens to be put by your browser.

As for your question, it may be that using **File > Open** will work whereas direct passing from your browser will not.
[img]http://i268.photobucket.com/albums/jj22/Rob_0edab8/Spacer.gif[/img]

---

### Post by jtreach on 2008-08-26
Thanks for your help, I am currently getting my brother (the person with the problem) to apply a similar solution to the one you have described (right clicking torrent links and selecting 'save as' and then opening with utorrent), but it's still a tad annoying for him.

Shame utorrent isn't native to Ubuntu really.

Thanks for the reply though :-D

---

### Post by Scunge on 2008-08-26
If you like uTorrent, you could try *KTorrent*. Quite similar.
[img]http://i268.photobucket.com/albums/jj22/Rob_0edab8/Spacer.gif[/img]

---

