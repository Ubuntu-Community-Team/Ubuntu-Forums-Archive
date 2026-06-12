---
title: "Ubuntu 8.04.1+Compiz --&gt; I want water effects on desktop"
date: 2008-07-20
forum: General Help
---

### Post by s3a on 2008-07-20
I saw on a youtube video a while ago, there was an effect ONLY ON THE DESKTOP (on top of the wallpaper/not on every window) of when you click it's like water moving as if you were like touching it from on top or like throwing a rock or whatever on it, can anyone help me achieve that?

Thanks in advance!

---

### Post by YaroMan86 on 2008-07-20
Should be part of the water effects in Compiz. Check your keybindings.

---

### Post by s3a on 2008-07-20
What are keybindings? And where do you check your water effects?? The only ways that I know of manipulating Compiz is through the program "Ubuntu Tweak" as well as clicking on "System-->Preferences-->Appearance-->Visual Effects.

---

### Post by wenuswilson on 2008-07-20
go to a terminal and type "ccsm" or hit alt+f2 (run app) and type it in, scroll down to effects and theres a bunch of manipulations you can do, including the water effect.

---

### Post by Portable_Jim on 2008-07-20
> **s3a said:**
> What are keybindings? And where do you check your water effects?? The only ways that I know of manipulating Compiz is through the program "Ubuntu Tweak" as well as clicking on "System-->Preferences-->Appearance-->Visual Effects.
See this post: [http://ubuntuforums.org/showpost.php?p=5419088&postcount=3](http://ubuntuforums.org/showpost.php?p=5419088&postcount=3)

---

### Post by s3a on 2008-07-20
When I run ccsm, it works but I get:

[B]deniz@deniz-desktop:~$ ccsm
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
deniz@deniz-desktop:~$[/B]

Having Compiz running sometimes renders my windows unclickable however for pidgin when it got unclickable I minimized it to tray and brought it back and it worked but for firefox, I have no idea what to do. Does anyone understand this problem and know how to fix it?

And enabling water effects, doesn't make splashy desktop when I click on the wallpaper :(.

---

### Post by DaymItzJack on 2008-07-20
You have to activate the rain by holding ctrl+super (default binding). However I don't think there is an option on what windows it can and can't go on.

---

### Post by s3a on 2008-07-20
That water effect works! But, I just don't like how I have to dedicate energy to make the effect if you know what I mean. Like I want to do what I normally do and experience the effects without wasting time and energy. Would it be possible to have it _constantly_ rain on top of my wallpaper (basically on my desktop)? I do not want rain on my other windows, ONLY on my desktop.

---

### Post by DaymItzJack on 2008-07-20
> **DaymItzJack said:**
> However I don't think there is an option on what windows it can and can't go on.



As for the "rain" effect, use shift+F9, it will rain in drops randomly, but still not only on desktop.

---

### Post by wenuswilson on 2008-07-20
not that i know of, you might be able to find an interective wallpaper somewhere to do such an effect (never found any personally but i've heard they exist).
my friend found one with the sun changing position throughout the day, might have been official ubuntu stuff, not sure.

anyway, i got the compiz fusion icon so if it doesn't load (or freezes) for whatever reason you can resfresh it, that's all it's really good for.

---

### Post by steveneddy on 2008-07-20
Please install

Compiz_Config-Settings-Manager

and play with that.

```
sudo apt-get install compizconfig-settings-manager
```

---

