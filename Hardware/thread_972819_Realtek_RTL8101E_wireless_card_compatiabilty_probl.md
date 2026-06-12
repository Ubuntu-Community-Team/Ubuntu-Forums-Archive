---
title: "Realtek RTL8101E wireless card compatiabilty problem. r8169 ?"
date: 2008-11-06
forum: Hardware
---

### Post by BelovedSe7en on 2008-11-06
My greetings to all !
I have just had my first encounter with Linux about 18 hours ago, and by first I mean *first*, as in I haven't even seen anyone use it before. So I call upon you to bear with me if I ever sound like I'm mentally incapable.

I was quite satisfied with Ubuntu's performance until I tried to set up the wireless connection, Apparently my wireless card, a Realtek RTL8101E, apparently isn't detectable by Ubuntu.The Linux driver can be found [here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false").

After reading a number of articles, I attempted to install it following the "read me" instructions, due to my lack of experience however, it took me a good while to eliminate the process of r8169, which I take is another driver blocking my card ? 
Regardless, it all went well, when I tried to copy the actual tar file -and the Winrarly extracted version of it- I couldn't by any means paste it in the root, or any other directory branching from it, except /home/beloved, which I was logged in as. 
I tried to log in as root, failing miserably. So I decided I'd go with "sudo bash" which made things a little harsher for me. I copied the tar file into /home/beloved and extracted it, when I found my way into the extracted folder with terminal, when I apply "make clean modules" and whatever comes next, it gives me an... Error, it's a whole lot of gibberish with an "Error2" at the end of it.

Also, the read me states : "If you are running as target Kernel"
What could that be ?
Also, as most of you have figured, when I apply "sudo lsmod | r8101", Nothing.

Any help I will gratefully appreciate, a man cannot live without internet, save me the suffering of having to use my brothers computer, or rebooting every other second to use... Vista =(

Cheers..

---

