---
title: "Fingerprint scanner - A different behaviour"
date: 2008-08-19
forum: General Help
---

### Post by robz0rz on 2008-08-19
Hello all

I have a ThinkPad T61 and I installed Ubuntu 8.04 Hardy (using gnome) on it as my OS. The laptop came with a fingerprint reader. Through browsing the internet (including these forums) I managed to install the correct things and edit the correct file (*/etc/pam.d/common-auth*) to use my fingerprint scanner.


However:
The resulting behavior was not really what I wanted... So I changed the *common-auth* file back to how it was. I was hoping someone on these forums could help me achieve the behavior that I want.


[LIST]
[*]When logging in, I had to type in my name, and I was able to swipe my finger instead of typing in my password. This didn't make much sense to me. Why should I type in my name? Isn't my fingerprint already my identification? I feel like just swiping my finger on the logon screen should be enough to login, seeing every fingerprint is unique.
[*]The only other place I would like to be able to swipe my finger as a form of identification is when unlocking the screen. I don't like how *sudo* told me to swipe my finger, I'd much rather just type in my password for *sudo* and other administrative tasks.
[/LIST]

I hope that someone can help me to get the desired behaviour of the fingerprint scanner. Thank you in forward,

-- Rob

---

### Post by antknee869 on 2008-08-19
How did you get the reader working?
Thanks

---

### Post by robz0rz on 2008-08-19
[These instructions]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_Release_Candidate_on_a_ThinkPad_T61#Fingerprint_Reader") helped me setting everything up, but I had to try a few different entries for */etc/pam.d/common-auth* from [this thread]("http://ubuntuforums.org/showthread.php?t=775217&highlight=thinkpad+fingerprint") in order to get everything working. I might write a full description of how I got it to work exactly some other time.


My own problem still persists. Can someone please help me getting my desired behavior? Thanks :)

---

