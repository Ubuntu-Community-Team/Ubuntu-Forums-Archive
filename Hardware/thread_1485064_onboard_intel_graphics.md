---
title: "onboard intel graphics"
date: 2010-05-16
forum: Hardware
---

### Post by Ariakkas on 2010-05-16
ive been looking everywhere...for awhile now, trying to figure out why i couldnt get desktop effects to work. 

and i think ive got it nailed down.

it seems my onboard intel chip is blacklisted by compiz, which in previous versions of ubuntu was fine because i could use the compiz manager to skip the blacklist check, and everything worked fine.

now in 10.04, it seems ubuntu doesnt use the compiz manager, and instead hardcodes the blacklist, meaning the only way to unblacklist it, is to use a hex editor. now im a smart person, but a hex editor is just way over my head.

now i see why they got rid of the "linux for human beings" slogan, cause im gonna have to learn to speak machine if i want to use it.

and my question being, is there another work around that i dont know about?

---

### Post by mikewhatever on 2010-05-16
If compiz blacklists your graphics card, it might be for a reason. 'Intel on board' doesn't always mean 3d capable, and providing the model number should be beneficial.

---

### Post by Ariakkas on 2010-05-16
im not trying to use my onboard graphics for 3d acceleration, i have a NVIDIA GEforce fx5200, that i use. i simply want to disable my onboard graphics, as compiz is detecting 2 video cards and that makes it drop a deuce.

i tried disabling it in my BIOS, but the only options i have are for 8mb or 1mb of memory going to the onboard card, or a "primary" card which i have set to PCI.

---

### Post by mikewhatever on 2010-05-16
Why didn't you say so in post #1?

---

### Post by Ariakkas on 2010-05-16
i dont see how its particularly relevant to my question.


my question is how to blacklist my video card in compiz. whether im using it or not is irrelevant.

i didnt ask how to get my integrated graphics card to work, i asked how to blacklist it.

---

