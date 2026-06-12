---
title: "How to set up a PHP Enabled, Multi-Website Development Environment"
date: 2008-12-02
forum: General Help
---

### Post by MrLeN on 2008-12-02
This is a tutorial which explains how to change your localhost development environment from your bookmarks. Simply click your bookmarks, select a site, and your localhost will be configured to run that website!

----How to set up a PHP Enabled, Multi-Website Development Environment 

I have been using Windows for 10 years. However, because of the fact that if I have to use windows for 10 more minutes I am going to leap off a bridge, I reformatted my computer a week ago and installed Ubuntu. I don't really know a WHOLE lot about Linux (particularly the OS), but I am a web developer and I have always used Linux servers. So, I know a few commands and stuff and the basic idea for how everything works. 

On Windows, I used to use [EasyPHP](http://www.easyphp.org/) for a PHP enabled development environment. I have used it for quite a few years (I can't remember exactly how many, but more than 5), and it successfully took care of all my local development needs. Basically, I simply created a new EasyPHP installation for each of my 50+ websites and made a shortcut to each of the exe's on a folder within my startup menu. I would simply click the link to the site I wanted to work on, and I had a localhost all ready to go for that website.

Now, I am using Ubuntu and I wanted to set up a similar system for me to work on. It took a bit of research and a little bit of messing around, but I have come up with a really cool way to do practically the same thing. Except it's much better :)

WARNING: I do realize that this tutorial is nothing short of "unconventional". However, it works for me. It works perfectly. It's a simple solution which took me an afternoon to set up, knowing very little about Ubuntu. So my best guess is that it will be an easy to set up solution for anyone else who has 50+ PHP websites and needs a local development environment for each of them.

I also understand that there are special virtual website packages and stuff for Ubuntu and Linux, etc.. but the thing is, I am a web developer -- not a system administrator, and to be quite frank, I really can't be bothered looking into all that. I have absolutely no wish to become a system administrator. My head is already too full of other web development related problems, which are already time consuming.

NOTE: I do fully expect seasoned system administrators to want to stalk me and cut my head off and all that, for adding this article. But I guess, at the end of the day -- it works for me, and I am sharing it in case there are other web developers who'd like to set something similar up.

HERE'S HOW I CREATED MY PHP ENABLED, MULTI WEBSITE DEVELOPMENT ENVIRONMENT:

1). I installed the server stuff. Basically, just follow [these instructions](http://ubuntuexperiment.wordpress.com/2008/11/10/installing-apache-php-mysql/) .. no need for me to rewrite it all here.

2). Once I had my server running, I typed [http://localhost](http://localhost) in my browser, and I got a message saying "It Works!".

3). So then I created a place to keep my websites. So I created 2 websites:

Places > Documents > My Websites > [www.website1.com](www.website1.com)
Places > Documents > My Websites > [www.website2.com](www.website2.com)

Note: "Places" is on the bar at the top of your screen.

4). Then I created an index file in each of the website folders, saying: "This is website 1" (for website 1) and "This is website 2" for website 2.

5). Then I wrote this script and added it to /usr/share/chsl

Note: I created the folder chsl myself. It stands for change symbolic link :)

Then I created a symbolic link for the chsl folder, and pasted it into the website folders. ie:

Documents > My Websites > [www.website1.com](www.website1.com) > chsl 
Documents > My Websites > [www.website2.com](www.website2.com) > chsl

note: Above "chsl" is a LINK to /usr/share/chsl, not a folder.

6). Then I created this script (as I am a web developer (ie: not a system administrator), it wasn't so hard) :)

```

<?php
if (empty($_GET['website'])) {
if ($handle = opendir('/home/USERNAME/Documents/My Websites')) {
    while (false !== ($file = readdir($handle))) {
        if ($file != "." && $file != "..") {
            echo '<a href="http://localhost/chsl/index.php?website='.$file.'">'.$file.'</a><br />';
        }
    }
    closedir($handle);
    die();
}
}
$path_to_link = '/home/USERNAME/Documents/My Websites/';
$new_website = $_GET['website'];
$link = '/var/www';
$target = $path_to_link . $new_website;
unlink($link);
#echo $target . $link;
symlink($target, $link);
#echo(readlink($link));
header('Location: http://localhost/');
?>

```

Note: Change USERNAME to your OS username!

Save that script in:  /usr/share/chsl/index.php

7). Delete the folder:

/var/www

Copy a link of the folder:

Documents > My Websites > [www.website1.com](www.website1.com)

Paste it into:

/var

Rename it to www (as it will have been "Link to www.website1.com")

Also, at this stage make /var fully writable (because the script above needs to be able to create symlinks in it).

8). In your browser, go to:

[http://localhost/chsl/index.php?website=](http://localhost/chsl/index.php?website=)

..and bookmark that page. Add the bookmark to your browser links bar for easy access, so that you can simply click it to get to the page.

9). click the bookmark, and you will be presented with a page that says:

[www.website1.com](www.website1.com)
[www.website.com](www.website.com)

..if you click one of those sites, your localhost will be configured to run that site. Then if you want to work on another website, simply click your bookmark again, select the site you want to work on and Bob's your uncle! :D

---

Notes: To add a new website, you need to add it to:

Documents > My Websites

But make sure that each new website has a link to:

phpmyadmin | /usr/share/phpmyadmin/
chsl | /usr/share/chsl/

---

System administrators, please don't stalk me. Personally, I think this is a cool system. It allows me to work on multiple websites without fuss (besides the 15 or so minutes it takes to set the above system up) :D

[COLOR="Red"]P.S. I typed this entire tutorial from memory, so it's possible I may have missed a step or forgot something. If you try to set this up and hit a problem, please leave a note. I will double check the part where you got stuck. But I think it's all there..[/COLOR]

---

