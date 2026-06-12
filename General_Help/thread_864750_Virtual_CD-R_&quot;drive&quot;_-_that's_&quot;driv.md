---
title: "Virtual CD-R &quot;drive&quot; - that's &quot;drive&quot; not mounted ISO image"
date: 2008-07-19
forum: General Help
---

### Post by zd3nik on 2008-07-19
I, foolishly, purchased a few songs on iTunes.  And I am now the proud owner of... nothing.  At least that's how Apple would have it.

I would like to actually be able to listen to the music I lawfully bought without having to boot into windows, which I have installed under a VirtualBox VM so I can use Visual Studio.

Anyway, Apple has managed to get ahead of QTFairTunes and the like so I can't just remove the encryption from my music.

So, as far as I've been able to find, using a virtual "CD-R drive" such as NoteBurner ($40) and making iTunes burn to this virtual "CD-R drive" (notice I'm saying "CD-R drive", not mounted ISO) seems to be the only way to remove the encryption from my music that doesn't involve wasting several CD-Rs.

Trouble is I don't want to pay $40 to be able to listen to music I already paid for.

So I was hoping there is a way to create a virtual "CD-R >>drive<<" in linux that I can just point VirtualBox at and viola: VirtualBox will make windows think there is a new CD burner "drive" in the system, which I can then make iTunes burn my music to.

I've seen quite a few posts from people asking for the same thing.  But pretty much every responder has missed the point and gone on to explain one of the 50+ ways to mount an ISO image in linux.  But if you're paying attention you've probably guessed that mounting an ISO image is not going to solve this problem.

I and countless other saps that were foolish enough to "buy" music from iTunes need a way to make a virtual "drive" that looks like a CD-R or CD-RW burner with a blank disk in it so that we may take proper ownership of the music we've purchased.

Thanks in advance for reading this rant, and thanks again if you can actually offer a solution to this problem - that does not involve simply mounting an ISO image, unless of course your method of doing so results in that image showing up as a CD-R drive with a blank disk in it...

:-({|=

Z

---

### Post by PoopLoops on 2008-07-20
So let me get this straight, you can burn from iTunes onto a CD, but even then there is too strong encryption to just rip the disc again?  I don't see how a regular virtual CD-R would help with this.

Ummm... is there a way to get a regular CD-R drive to think that some random folder say on your Desktop is actually a CD?

EDIT:  No, I guess it would be the burning software that would do that...?

---

### Post by ddales on 2008-07-20
[http://mediakey.dk/~cc/remove-itunes-drm/](http://mediakey.dk/~cc/remove-itunes-drm/)

---

### Post by krsmit0 on 2008-07-20
i thought i read somewhere (can't find it now) that cd burning isn't supported by virtualbox.

EDIT:  This is what i found in the user manual...

  Using the host drive normally provides a read-only drive to the guest. As an ex-
perimental feature (which currently works for data only, audio is not supported), it is
possible to give the guest access to the CD/DVD writing features of the host drive (if
available):
VBoxManage modifyvm <vmname> -dvdpassthrough on

---

### Post by zd3nik on 2008-07-20
> **PoopLoops said:**
> So let me get this straight, you can burn from iTunes onto a CD, but even then there is too strong encryption to just rip the disc again?  I don't see how a regular virtual CD-R would help with this.

You can burn the music to a CD-R and that removes the encryption, which is why burning to a virtual CD-R also works.  I would just rather do the virtual drive than put all the wear and tear on my CD burner, not to mention wasting a lot of CD-Rs.

Thanks,
Z

---

### Post by ymo on 2008-07-20
It won't save wear on your burner but using a CD-RW disc will allow you to just keep reusing the same disc instead of wasting CD-R blanks.

---

### Post by Mister.Vash on 2008-07-21
Take a look at this product, Virtual CD, it looks like they have a demo that would keep you from having to shell out money.  

[http://www.virtualcd-online.com/vcd/apps/overview/original.cfm?lg=0](http://www.virtualcd-online.com/vcd/apps/overview/original.cfm?lg=0)

It reports that it supports "Up to 23 virtual CD/DVD burners"

You could try to installing that on your VirtualBox VM and see if it works

I don't know if any free versions of this, so you may need to look for one if you keep buying the itunes songs.  But this may take care of the ones that you have right now.

---

### Post by AndyCee on 2008-07-23
I'm certain there's a short, simple CLI way of doing this...

---

