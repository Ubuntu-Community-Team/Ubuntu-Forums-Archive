---
title: "Apple wireless bluetooth keyboard and mouse dual-boot (Ubuntu + OS X)"
date: 2016-02-12
forum: Hardware
---

### Post by Karl_Hungus on 2016-02-12
I have synced up bluetooth in Ubuntu 14.04 then OS X (El Cap) second followed by finding the "linkkey" file at[COLOR=#666600][FONT=monospace]/[/FONT][/COLOR][COLOR=#000088][FONT=monospace]private[/FONT][/COLOR][COLOR=#666600][FONT=monospace]/[/FONT][/COLOR][COLOR=#000088][FONT=monospace]var[/FONT][/COLOR][COLOR=#666600][FONT=monospace]/[/FONT][/COLOR][COLOR=#000000][FONT=monospace]root[/FONT][/COLOR][COLOR=#666600][FONT=monospace]/[/FONT][/COLOR][COLOR=#660066][FONT=monospace]Library[/FONT][/COLOR][COLOR=#666600][FONT=monospace]/[/FONT][/COLOR][COLOR=#660066][FONT=monospace]Preferences[/FONT][/COLOR][COLOR=#666600][FONT=monospace]/[/FONT][/COLOR][COLOR=#000000][FONT=monospace]blued[/FONT][/COLOR][COLOR=#666600][FONT=monospace].[/FONT][/COLOR][COLOR=#000000][FONT=monospace]plist[/FONT][/COLOR][COLOR=#000000][FONT=monospace][SIZE=4] and next I flipped all the numbers in reverse pairs and added them to my [/SIZE][COLOR=#333333]cd /var/lib/bluetooth/a8:86:dd:a4:d6:f8/linkkeys [SIZE=4]in Ubuntu[/SIZE] [SIZE=4]but [/SIZE][/COLOR][SIZE=4]its not working for me.
[/SIZE]

    LinkKeys =     {
        "a8-86-dd-a4-d6-f8" =         {
            "1c-1a-c0-e2-75-07" = <efacfb00 8e15a4a6 c67e9365 3c0e2487>;
            "28-cf-e9-7a-f4-86" = <cc06ea32 5a6a31fc 028abfeb 0b932e83>;
            "84-38-35-39-76-1f" = <abe06bd8 6d00ac5f 3fb52bd8 8f122b15>;


Thanks, hope someone can help.
[/FONT][/COLOR]

---

