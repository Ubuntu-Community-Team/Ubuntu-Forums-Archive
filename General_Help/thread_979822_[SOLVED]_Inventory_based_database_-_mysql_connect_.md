---
title: "[SOLVED] Inventory based database - mysql connect error upon setting it up."
date: 2008-11-12
forum: General Help
---

### Post by greavette on 2008-11-12
Hello,

I've been using this post:
[http://ubuntuforums.org/showthread.php?t=508053](http://ubuntuforums.org/showthread.php?t=508053)
to install the following web based inventory system:
[http://www.inventory-management.org/](http://www.inventory-management.org/)

The ubuntu forum post has been really helpful, but I've hit a problem and I don't know how to get around it.  Here's what I've accomplished so far:

I've downloaded the following LAMP appliance:
[http://virtualappliances.net/products/lamp.php](http://virtualappliances.net/products/lamp.php)

I've successfully connected to the LAMP with phpmyadmin and have successfully completed the following steps from the previously mentioned ubuntu forum post (post #5):
[http://ubuntuforums.org/showpost.php?p=3080967&postcount=5](http://ubuntuforums.org/showpost.php?p=3080967&postcount=5)

I then modified my site.xml file with the following information:
```
	<database type="mysql">
		<server>10.100.159.160</server>
		<login>user</login>
		<password>test</password>
		<default>inventory</default>
	</database>
```
where I initially setup an id of 'user' as my new account.

I'm running this lamp appliance from a windows XP pc, so I used WINSCP from:  [http://winscp.net/eng/index.php](http://winscp.net/eng/index.php) (version 4.1.7) to connect to my Lamp Appliance.  

Using WINSCP, I figured out that the inventory management files from the zip file had be copied to my appliance in this folder:
/var/www/html/inventory (where I created the folder called inventory).

I then created an .htaccess file in this folder with the following:

```
<Files ~ "^\.ht">
Order allow,deny
Deny from all
</Files>
```

So far so good.

I then discovered I had a problem with /var/www/html/inventory/lib/common.php where the function fputcsv gave an error.  I googled and found this post:  [http://www.phpfreaks.com/forums/index.php/topic,96308.msg385765.html#msg385765](http://www.phpfreaks.com/forums/index.php/topic,96308.msg385765.html#msg385765) where I then modified the common.php file as follows (Lines 931 to 935):

```
}#end f_put_csv()

function f_put_csv ($fp, $array, $deliminator=",") {
	return fputs($fp, putcsv($array,$delimitator));
}#end f_put_csv()
```

Essentially changing fputscv to f_put_csv.  

Again, so far so good.  But here is where I have a problem (finally!).

When I try to login with:  [http://10.100.159.160/inventory/](http://10.100.159.160/inventory/) I get the following error:

> Warning: mysql_connect() [function.mysql-connect]: Lost connection to MySQL server at 'reading initial communication packet', system error: 111 in /var/www/html/inventory/lib/database.php on line 85

Warning: mysql_error(): supplied argument is not a valid MySQL-Link resource in /var/www/html/inventory/lib/database.php on line 85
CDatabase::Connect() error 

The Ubuntu forum post I've been using also mentions having this problem, but it says to do the following:

> Connect to your mysql database with your host's interface software and look for the name of the server host.

It'll be something like p41mysql71.secureserver.net (a sub-domain of your actual host is what I'm getting at).
Change out 'localhost' for that variable and it should work.

My question is, how do I connect to my mysql database?  Do I use the phpmyadmin tool again like I did when I first created the database?  Where do I find the name of the server host?  Please be specific on what I do and where I look...I'm a newbie working with LAMP appliances and using mysql and web page creation.

I also don't know if I've correctly setup the .htaccess file.  When I put in [http://10.100.159.160/inventory/site.xml](http://10.100.159.160/inventory/site.xml), I do not get a forbidden message

I've made it this far and I feel like I'm so close to getting this working.  I've put a lot of effort into working through my problems so far to get this going, but I'm at a dead end here.  If anyone has an idea of how to get around this, I would really appreciate the help!

Thanks!

---

### Post by fatphilthethird on 2008-11-12
Fat

Hmm, looking through they mysql site, you should be using localhost, which makes sense as both the php file and the mysql server are on the same machine:

[http://forums.mysql.com/read.php?52,151255,156258#msg-156258](http://forums.mysql.com/read.php?52,151255,156258#msg-156258)

What server does it actually specify in /var/www/html/inventory/lib/database.php ?

---

### Post by greavette on 2008-11-12
Hello Fat,

Thanks for the response!

I don't think the database.php specifies a database..I think the database variable comes from my site.xml file.  Here's the Connect function in database.php:
```

	function Connect($connect_params = "") {
		extract($connect_params);
		//resource mysql_connect ( [string server [, string username [, string password [, bool new_link !!! [, int client_flags ]]]]] )
		$this->conn_id = mysql_connect($server,$login,$password,TRUE) or die("CDatabase::Connect() error " . mysql_error($this->conn_id));

		if ($default != "")
			$this->SelectDB($default);
	}
```

I think you are right, that I should be using localhost.  I've updated my site.xml with 'localhost' instead of the ip address I had earlier, and now I receive this error message:

> Warning: mysql_connect() [function.mysql-connect]: Access denied for user 'user'@'localhost' (using password: YES) in /var/www/html/inventory/lib/database.php on line 85

Warning: mysql_error(): supplied argument is not a valid MySQL-Link resource in /var/www/html/inventory/lib/database.php on line 85
CDatabase::Connect() error 

It would seem I haven't given the correct access to my userid 'user' since access has been denied.  Any idea how I messed up the access?

Thanks!

---

### Post by greavette on 2008-11-12
Hey, I got it to work!

I logged back in with phpmyadmin and took a look at my privileges.  My host associated with my id of 'user' was '%' for any host.  I changed this to localhost.  I think this change in combination with the change to my site.xml file to use 'localhost' instead of an ip address made it work.

I had to login with 'admin' and password 'test' (no quotes of course) and I'm good to go.  I can then add as many other accounts as I like.  I'm not sure the point of adding my account of 'user' since I couldn't login with this account and had to use 'test'.

I'll mark this as complete.  Hopefully I've given enough detail in this post to help others who want to use this inventory database.  I'm sure there are more robust ones out there, but this one is perfect for our small business.

---

### Post by fatphilthethird on 2008-11-13
Depending on what access your user account has, it may well not be able to log into phpmyadmin. I think I had a similar problem and it was only those users that had full priviledges that could log in. Which does kind of make sense.

The point of the 'user' account is so you have an account without full priviledges, i.e. cannot create or destroy whole databases, to use within your php script. You should never use root or an equivalent strength user account within your php scripts for security reasons.

Glad you got it sorted. Seems a very strange set up to me to configure a php mysql connection from an xml file, but I'm sure the original developers had their reasons.

Fat

---

