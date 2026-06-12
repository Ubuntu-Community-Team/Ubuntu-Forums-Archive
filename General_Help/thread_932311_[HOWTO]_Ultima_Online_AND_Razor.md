---
title: "[HOWTO] Ultima Online AND Razor"
date: 2008-09-28
forum: General Help
---

### Post by Sleepys on 2008-09-28
Alright, I'm making this HOWTO because I've not been able to find one, and I recently got Razor working for me, which seems to be nearly unheard of. I'd also like to add up front there are glitches, which I've mentioned at the end. If you want to report glitches, just add a reply and I'll get an e-mail. Also, I've only got this to work for a free server, I don't know how successful this will be on Origin servers or other free servers. If you get it to work with other versions, post your success.

Since I'm making this thread active, I'll TRY to check it daily for new posts, and reply to them while adding information to the first post.

What I used:
Ubuntu Ubuntu 8.04.1 Hardy Heron
Ultima Online Version 4.0.11c
Razor version 1.0.0 (NOT the updated version)
Wine
Winetricks

Ok, since you should already have Wine, I'll assume you do. If not, it's easy to get and I'm sure you can easily search the internet for it. So we'll begin with step one:

**Step One**
You'll encounter a problem if you try to install Razor without a Windows system called .netframework. However, Linux normally doesn't support it and neither does Wine, that's where Winetricks comes into play. I'm not going to write a HOWTO on it, but there is one already written, and it's simple.
[Winetricks HOWTO]("http://wiki.winehq.org/winetricks")

**Step Two**
You should install Ultima Online BEFORE Razor, but it is not necessary. Installing UO was simple for me, it simply just worked. However, a lot of people play on free servers and encounter issues logging in. I'll see if I can help. So I've added a FAQ section at the bottom for questions asked on this thread.

**Step Three**
Now I'll make one more assumption, that you were successful in getting Winetricks and .netframework installed on Wine. Next is installing Razor, which can be done from [here]("http://www.runuo.com/razor/download.php"). Make sure to download version 1.0.0, it's the bottom link under the current one.

**Step Four**
Run Razor, and try to log in, if it doesn't advance past "Verifying Account", or "Connecting", chances are you have a duplicate file. Simply find and delete all duplicates (as explained in FAQ section), and rename the duplicate you saved to be all lowercase, that will prevent duplicates later on.

At this point, you SHOULD be able to get it to run, hook, and play just fine, with some minor glitches. I've noticed only two so far. In the "Glitches/Errors" section.

Thanks for any added information you can provide, sorry this isn't more detailed, it's my first HOWTO.
-Sleepy




--------------------------------
Glitches/Errors
--------------------------------
1. The title bar of Ultima Online will not display your regent/bandage count, this I've yet to find a way to fix.

2. Do not push control or alt key while the Razor window is active, it will cause an error. I'm not sure why this error is caused for I've not researched it yet. Simply hit continue if you accidentally get it and it should just continue to work.
--------------------------------




--------------------------------
FAQ
--------------------------------
Question: Every time I run Ultima Online, it turns gray and freezes
Answer: Check your UO client version and make sure it's the EXACT same with the one the server uses (Don't use UOPatcher UNLESS YOU ARE PLAYING ON Origin!).

Question: When I get to "Verifying Account", is just locks up, how come?
Answer: Ah, this is going to be a hard step. You may have two files with the same name. In Linux, CLIENT.exe, Client.exe, and client.exe are three different files, that's because they're in different case forms. Any duplicate files in you Ultima Online folder will eventually cause issues, so go through it and delete ANY file that has the EXACT same name and extension. Make sure to only save the file that is provided by the free server if it applies.
--------------------------------

---

### Post by mholland on 2008-12-16
The above works for me with some few additions.

You can use the latest patched client and the latest version of razor now successfully given you have installed the latest version of WINE and WINETRICKS.

**TIPS:**
1. Run wine in an emulated desktop with ultima, it tends to want to stay on top of all of your other running windows and if you minimize it you will notice severe glitches. Keeping Ultima encapsulated in an emulated desktop that can be setup in wine configuration is the way to go. Just set it to match your desktop resolution or slightly lower. Doing this will allow you to minimize and close the application properly.

2. SYSTEM -> APPEARANCE -> VISUAL EFFECTS: Set the effects to no ne, if you noticed drop frames and poor performance out of ultima you will notice improved game speed after making this change. 

3. Razor will likely give you issues with specifying a custom port with a server your trying to connect to. Make a backup of login.cfg in your ultima directory and modify login.cfg to reflect the settings of the server you wish to connect to.

ENJOY ULTIMA! If I run into any more helpful advice I will post here. Game runs perfect with absolutely no glitches here on Ubuntu 8.10 Intrepid w/ latest release of WINE and WINETRICKS.

:guitar:):P:guitar:

---

### Post by Sleepys on 2008-12-17
Thanks for the tip, always good to know people find better ways to do things and make them easier.

---

### Post by Matspoiss on 2009-01-27
Hello! Having done all the necessary steps, I still experience a glitch running Razor. I have Intrepid Ibex and the latest wine/winetricks and Razor. 

I'm quite new to Linux, but I tried running Razor with a terminal and i think here's the problem:

```
Unhandled Exception: System.AccessViolationException: Attempted to read or write protected memory. This is often an indication that other memory is corrupt.
   at System.Drawing.SafeNativeMethods.Gdip.GdipCreateFontFromLogfontW(HandleRef hdc, Object lf, IntPtr& font)
   at System.Drawing.Font.FromLogFont(Object lf, IntPtr hdc)
   at System.Drawing.Font.FromHfont(IntPtr hfont)
   at System.Drawing.SystemFonts.get_DefaultFont()
   at System.Windows.Forms.Control.get_Font()
   at System.Windows.Forms.ComboBox.get_PreferredHeight()
   at System.Windows.Forms.ComboBox.get_DefaultSize()
   at System.Windows.Forms.Control..ctor(Boolean autoInstallSyncContext)
   at System.Windows.Forms.ComboBox..ctor()
   at Assistant.WelcomeForm.InitializeComponent()
   at Assistant.WelcomeForm..ctor()
   at Assistant.Engine.Main(String[] Args)

```

I searched for the problem on the net and found others with the same issue but no solution:

[http://www.runuo.com/forums/razor-cutting-edge-uo-assistant/92674-how-run-razor-ubuntu-linux.html](http://www.runuo.com/forums/razor-cutting-edge-uo-assistant/92674-how-run-razor-ubuntu-linux.html)

---

### Post by pacificflows on 2009-04-17
Hello.

I have followed your guide, and the .netframework will not install using wine.

Perhaps I'm not using winetricks correctly? I installed dotnet11 and dotnet20, which were the only things on the winetricks list I could discern as having anything to do with a .netframework.

I am very frustrated.

Please help.

---

### Post by Trizzy on 2010-03-13
Assigning the .winetrickscache folder (a hidden file in your home folder IF winetricks is installed) to a drive letter in the Drives tab of winecfg fixed this problem for me. Before the fix, .net2 would end the installation prematurely.

---

### Post by drbrontosaurus on 2010-06-20
OK, I've managed to get UO and Razor running. I put in my login and it says there was a problem communicating with origin, restart and try again.

I tried editing the login.cfg thinking it was still trying to connect to Origin instead of the shard I play. It didn't work.

Any ideas?

---

