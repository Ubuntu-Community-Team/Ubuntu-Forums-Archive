---
title: "What is the theory behind file types?"
date: 2008-11-18
forum: General Help
---

### Post by epicbattle on 2008-11-18
I'm not a computer science major, so I am using the internet as schooling. I just a question on why files cannot be understood in different OS. (ie Why can't linux read .exe files without the WINE emulator). Likewise, why can't OSX or Windows read .deb or what have you. I may not have the correct understanding on the basic fundamental architecture of kernels. Or maybe it's a litigation issue? I dunno. If anyone has links as to how all this stuff works, and why it doesn't work I would be very interested in reading it.

---

### Post by 420shaggy on 2008-11-18
If you are really interested in this you should probably go to the library and pick up some book about the structure of each operating system because what you are asking is what CS students go to university for.  Essentially it can be compared to asking why can't someone who only speaks English read a Spanish book?  Program's like Wine emulate a Windows environment so Win programs can be installed on Linux - which is like get a translator so that you can read that Spanish book.

  A nice general summary of the differences between Linux and Windows can be found of course on wikipedia: [http://en.wikipedia.org/wiki/Comparison_of_Windows_and_Linux]("http://en.wikipedia.org/wiki/Comparison_of_Windows_and_Linux")

---

### Post by DGortze380 on 2008-11-18
> **epicbattle said:**
> I'm not a computer science major, so I am using the internet as schooling. I just a question on why files cannot be understood in different OS. (ie Why can't linux read .exe files without the WINE emulator). Likewise, why can't OSX or Windows read .deb or what have you. I may not have the correct understanding on the basic fundamental architecture of kernels. Or maybe it's a litigation issue? I dunno. If anyone has links as to how all this stuff works, and why it doesn't work I would be very interested in reading it.

You're question is a little mixed...

Linux, Windows and OS X are totally different operating systems. They function in fundamentally different ways. Thus, the programs that run on these system are (for the sake of argument) fundamentally different. The language example above is a good one. Why can't windows read a .deb? Because it's not a debian based linux distro. Why can't Linux read an .exe? Because it's not windows. The answer is as simple as that. 

Why can't you use a map of Paris, France to get to a hotel in New York City? Because your map contains information in the wrong format. Sure, it has streets and subways, but they're all in the wrong spot for the city you're in. Now if you use a map of NYC, then you get a hotel room just fine; or if you're in Paris and use your map of Paris, you also get a hotel room just fine. Switch the two, and you get nowhere. End result may be the same, but the paths are fundamentally different.

Now for the other half of your question, file types. .exe is not really a 'file type' as you were referring to it. It's an extension, used by windows, to identify an executable. A file type like .jpg or .mp3 can certainly be read by any OS that has the codecs to read it.

---

