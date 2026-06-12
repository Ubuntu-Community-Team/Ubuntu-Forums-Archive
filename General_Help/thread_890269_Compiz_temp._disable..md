---
title: "Compiz temp. disable."
date: 2008-08-14
forum: General Help
---

### Post by RevolutionMaster on 2008-08-14
I need to do this to fix the leaving fullscreen bug with games,.
I need to disable compiz automatically when a game starts, and afterwards, start compiz. Any help would be great!

---

### Post by isaacj87 on 2008-08-14
> **RevolutionMaster said:**
> I need to do this to fix the leaving fullscreen bug with games,.
I need to disable compiz automatically when a game starts, and afterwards, start compiz. Any help would be great!

Hey!

Perhaps, this can be of use to you?

[http://ubuntuforums.org/showpost.php?p=5307405&postcount=25]("http://ubuntuforums.org/showpost.php?p=5307405&postcount=25")

This *should* do what you need. :)

---

### Post by RevolutionMaster on 2008-08-14
> **isaacj87 said:**
> Hey!

Perhaps, this can be of use to you?

[http://ubuntuforums.org/showpost.php?p=5307405&postcount=25](http://ubuntuforums.org/showpost.php?p=5307405&postcount=25)

This *should* do what you need. :)
I'm fine until I get to this part :
> **ou only have to create the script once.**

3) Now you're going to create a wrapper application. Run these commands in terminal:

 	Code:
 	sudo mv /usr/bin/mathematica /usr/bin/mathematica.real 
**Keep in mind that I'm assuming that's the location for Mathematica's bin**

Then do this:

 	Code:
 	sudo touch /usr/bin/mathematica 
Now this:

 	Code:
 	sudo chmod 777 /usr/bin/mathematica 
and finally this:

 	Code:
 	echo 'compizswitcher mathematica.real $@' > /usr/bin/mathematica 
Done! Now, you should be able to run Mathematica and it will disable CF and notify you at the bottom that it has. After the program exits, CF will re-enable itself (and will notify you at the bottom). **Like I said, rinse and repeat for other applications if you want. You don't have to keep on creating the script. Just repeat everything past step 3, but substitute the bin name.** Hope this works for you. Here's where I found the information for this: [http://quietmint.com/blog/2008/06/ma...-cards-get.php]("http://quietmint.com/blog/2008/06/make-vlc-and-ati-graphics-cards-get.php")

I need to do this for Tremulous, and can't find what is needed.

---

### Post by isaacj87 on 2008-08-14
Hmm...Unfortunately, I don't have Tremulous installed. Any place I put "mathematica" should be replaced with "tremulous".

Try looking in /usr/bin and see if you can find a bin file for Tremulous.

---

### Post by RevolutionMaster on 2008-08-15
> **isaacj87 said:**
> Hmm...Unfortunately, I don't have Tremulous installed. Any place I put "mathematica" should be replaced with "tremulous".

Try looking in /usr/bin and see if you can find a bin file for Tremulous.
I tried this, but it didn't work. I don't really know where it is. The game is based on the Quake engine though. (If that helps)

---

### Post by Twilight in Zero on 2008-08-15
I just use this script:

```
#!/bin/bash
#  gamerun
#
#  Sun Oct 28 07:17:37 2007
#  Copyright  2007  Enrique Schiel
#  <ecschiel@yahoo.com.ar>

# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
# 
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU Library General Public License for more details.
# 
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor Boston, MA 02110-1301,  USA

CHANGE=0

if ps -e | grep compiz; then
    CHANGE=1
fi

if [ $CHANGE == 1 ]; then
    printf "Disabling advanced desktop efects...\n"
    /usr/bin/metacity --replace &
fi

printf "Running the game...\n"
$@ &
wait $!

if [ $CHANGE == 1 ]; then
    printf "The game is finished. Restoring advanced desktop efects...\n"
    /usr/bin/compiz --replace &
fi

exit 0
```

With this one, I only have to do, for example, to run ZSNES, "gamerun zsnes". Metacity will replace Compiz, the game will run, and after it's done, Compiz will come back. I've already modified all of my opengl game shortcuts with this.

I didn't make this script, but I don't remember where I got it from. The guy's name is up at the top of the script. I just changed its name and added exit 0 to the end.

---

