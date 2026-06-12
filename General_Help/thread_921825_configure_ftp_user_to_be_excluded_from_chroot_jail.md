---
title: "configure ftp user to be excluded from chroot jail  (proftpd)"
date: 2008-09-16
forum: General Help
---

### Post by Corrupter on 2008-09-16
Hello guys,

once again i am in need of your ever valuable knowledge and while i know the temptation will be to tell me that this is insecure or in some way degrading to my system, please i urge you to only answer the question if you have my solution.

I wish to specify a user the ability to navigate outside of his home directory.

Now, i know of some ways to do this and i'll state what they are and why they dont work for what i am trying to achieve.

i could specify that the directive DefaultRoot  ~ is deleted in the conf, but this would allow all users to migrate outside of their home.

I could specify a new home for my user, one that better accomodates where he should be, but then  he still would only be navigating inside his home directory.

The bottom line is that i am attempting to have an ftp administrator, one that could have rwx permissions for all the directories i wish him to handle and furthermore this user will have a desktop enviroment to be able to log in locally if he so chooses although ftp is the primary mode of communication.

i wish to use a user i already have set up as my initial user so i dont want to create a new user or a group for my existing user, but add him to one if he has to be for the folders he needs to access...

i know it sounds like the impossible, i am but a lamen, but if any of you free-thinkers out there want to give a stab at this feel free.





PS, i DID google search AND forum search and all the solutions they presented were the 2 i listed above.

---

### Post by forger on 2008-09-16
So in short, you want to limit all users except for some users.
You can do that if you specify a group in which you will add those users, read: [http://www.proftpd.org/docs/howto/Chroot.html](http://www.proftpd.org/docs/howto/Chroot.html) (hint: 3rd, 4th and 5th paragraphs :) )

edit: or here: [http://www.proftpd.org/docs/directives/linked/config_ref_DefaultRoot.html](http://www.proftpd.org/docs/directives/linked/config_ref_DefaultRoot.html) (check out the example)

You could learn and be more productive if you just read the manual, it really comes in handy when you're using it for server purposes: [http://www.proftpd.org/docs/directives/configuration.pdf](http://www.proftpd.org/docs/directives/configuration.pdf)

---

### Post by Corrupter on 2008-09-16
i honestly DO appreciate you answering my question directly, however you could have done it without trying to make it seem that my intellect is less than yours.  I DID browse through the manual and DID see this portion however mis-interpreted the section where it referenced the tilde, i took it to mean it was going to explain what it mean although i knew what it meant.  This has been known to happen inside the human species from time to time.

Thanks again.

---

### Post by forger on 2008-09-16
You simply haven't written in the post that you have read the manual, you mentioned google and forum search. I'm certainly not a psychic and I was playing safe by pointing you to the right direction.
I never attacked you personally, nor have I criticised your intellectual level. Maybe it sounded harsh in a very indirect way (which I neglected from my point of view), but interpret it this way: If anything, you won't miss that detail again, you'll always think of that guy that "put you down", which wasn't my intention nor my wish to do that :)
Finally, I never said I know anything more than you do, I'm a hobbyist and I like to give back to the community at my spare time. (I have in fact broken several machines through these forums or the IRC chat)

So once again: no offense, just recommending/suggesting.

---

