---
title: "Enabling playback of dvds without internet"
date: 2008-07-15
forum: General Help
---

### Post by pwolschen on 2008-07-15
My computer can't connect to the internet. However that's not a big deal. I just want to use it to play dvds. However i need to install the stuff to play the dvds. How could i do this without internet?

---

### Post by Taxman415a on 2008-07-15
Well you still need to install the same packages, so you need to download them some way. One way to do this is to run synaptic, follow the instructions to get all the packages you need and instead of selecting apply changes, go to the file menu and choose Generate package download script. Then copy that script to whatever machine does have internet access and download all the packages needed and then copy them back to the ubuntu box and install them.  Of course if possible getting internet would be better :)

Incidentally is there a way yet to buy legal DVD (in the US) playback software for Ubuntu?

---

### Post by pwolschen on 2008-07-15
I tried it but then it wont recognize the other parts. For example when i try to install ogle it tells me that it can't install because it cant find libdvdread3. However it is already installed. I have also tried installing vlc player but that also says that there is a problem and it wont find libdvdread3.

---

### Post by Taxman415a on 2008-07-15
Try to save the exact text of the commands you try entering and the output. From what you've written I don't know what to tell you. With the details I or others may be able to.

---

### Post by pwolschen on 2008-07-15
I wasn't using terminal. I found the various debian packages throughout the internet. I downloaded teh individual packages for libdvdread3 and ogle and vlc and a bunch of other ones but then it says that the dependency is not found and wont let me install.

---

### Post by Taxman415a on 2008-07-15
Right, but again, without the specific things you did and the specific error messages it's very hard to help. You mention dependencies not found and that is why I recommended the synaptic method. It will find all of the needed dependencies for you. That way you can download all of them.

---

### Post by pwolschen on 2008-07-15
I tried doing the synaptic method but i can't update the list of files. Most of the files aren't in synaptic unless its connected to the internet. Or am i missing something?

---

### Post by Taxman415a on 2008-07-15
That's true, the latest versions of everything might not be known to your synaptic version, but at least it will know what packages are needed. Then you can go about manually getting the latest versions of them for your version of Ubuntu. For the most part as long as the release you have installed is recent, there won't be that many packages that your synaptic doesn't know about, they'll just be a bit out of date.

I take it you have also seen [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

I'm now reallizing how tricky this is without internet access since you'll need to dl the libdvdcss2 package from medibuntu as well if it's legal in your area.

---

