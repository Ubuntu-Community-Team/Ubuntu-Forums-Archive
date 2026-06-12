---
title: "Update manager errors"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by TexMex657 on 2009-04-30
Error message from update manager:

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://switch.dl.sourceforge.net ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY BB837A65EB7A4D95

W: Failed to fetch http://switch.dl.sourceforge.net/sourceforge/bibus-biblio/./Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

I'm sure this can be fixed quite easily. I tried some of the other solutions from previous update manager error threads but couldn't get anything to work.

Thanks in advance.

---

### Post by krisjack on 2009-05-05
Hi there,

I had the same problem.  I think that the key has expired for this application.  Try going to the [sourceforge site for the project]("http://sourceforge.net/project/showfiles.php?group_id=110943&package_id=151072&release_id=600703") and then download the file named:

[COLOR=Blue]pmartino.gpgkey[/COLOR]

Once you have downloaded it, add the new key and remove the old one.  Here's one way to do so:

[COLOR=Red]System -> Administration -> Software Sources[/COLOR]
Click on the tab named [COLOR=Red]Authentication[/COLOR]
Click on [COLOR=Red]Import Key File[/COLOR]
Retrieve the [COLOR=Blue]pmartino.gpgkey[/COLOR] file that you downloaded

You can then delete the old key that you had for this application from the same [COLOR=Red]Authentication[/COLOR] tab.  Just find the key that has the name Pierre Martineau, select it from the list and click on [COLOR=Red]Remove[/COLOR].

This worked for me, I hope that it does for you too.

Happy referencing!
Kris

---

### Post by TexMex657 on 2009-05-05
Looks like that did the trick. Thanks for all your help!

---

