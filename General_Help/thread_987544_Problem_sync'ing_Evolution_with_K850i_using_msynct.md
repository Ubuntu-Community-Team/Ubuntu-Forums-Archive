---
title: "Problem sync'ing Evolution with K850i using msynctool"
date: 2008-11-19
forum: General Help
---

### Post by saxo28 on 2008-11-19
Hi all, my first post here. I'm a newbie to Ubuntu since about a week ago, but so far have managed to switch from WinXP pretty painlessly :) I hope I'm posting this in the right section, none of the other categories seemed to fit what I'm trying to do...

I found a guide [[COLOR="RoyalBlue"]here[/COLOR]](http://gronbaek.net/2008/03/10/synchronize-sony-ericsson-k610i-with-ximian-evolution-on-ubuntu/) to sync my SE K850i mobile with Evolution, but I'm having trouble getting it to work - can anyone help / tell where I'm going wrong please?

I followed the guide (using 'evok850i' as the name for the group to be sync'd), but when I tried to sync the phone it failed. I'm just trying to sync the calendar and contacts.

To start the sync I typed this:
> msynctool --sync evok850i --filter-objtype note --filter-objtype todo --conflict n

And I got this:
> Synchronizing group "evok850i" 
Member 1 of type evo2-sync just connected
Member 2 of type irmc-sync just connected
All clients connected or error
Member 1 of type evo2-sync just sent all changes
Member 2 of type irmc-sync just sent all changes
All clients sent changes or error
Member 2 of type irmc-sync committed all changes.
Member 1 of type evo2-sync committed all changes.
All clients have written
Member 2 of type irmc-sync had an error while calling sync done: Broken Pipe
Member 2 of type irmc-sync had an error while disconnecting: Broken Pipe
Member 1 of type evo2-sync just disconnected
All clients have disconnected
The sync failed: Unable to finish the sync for one of the members
Error while synchronizing: Unable to finish the sync for one of the members

On the phone I get a dialog saying 'connection lost' almost immediately once it starts to sync.

Any ideas?

Thanks.

---

### Post by saxo28 on 2008-11-19
Sorry I forgot to say I am trying to sync via bluetooth and I have already paired the phone with the PC.

---

### Post by snooze86 on 2009-07-18
Hi, I've the same problem with the K770i, have you solved it ?

For more Details:

I've had exactly done the same as saxo28. Syncing the contacts form evo to my mobile phone works, but not in the other direction.

---

