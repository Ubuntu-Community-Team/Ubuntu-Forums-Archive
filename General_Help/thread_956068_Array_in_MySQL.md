---
title: "Array in MySQL"
date: 2008-10-22
forum: General Help
---

### Post by Black Mage on 2008-10-22
I am trying to figure out how to design a database and I have come across using arrays in mysql. Basically what I am trying to create is a field that can hold multiple values without limit. For example, a table is created like this:

Primary Key: User_ID
First_Name
Last_Name
Favorite_Movies[1...x]

The x represents any amount of favorite movies. So I was wondering would an array be the best way to store infinite number of someone's favorite movies? And this is a MySQL database.

---

### Post by trwww on 2008-10-22
There is a pretty standard way to go about this with databases. The way you do this is with three tables: people, movies, and people_movies:

persons:
id
first_name
last_name

movies:
id
title
release_year

persons_movies:
id
person
movie

See this tutorial:

[http://code.google.com/edu/tools101/mysql.html](http://code.google.com/edu/tools101/mysql.html)

Todd W.

---

### Post by hyper_ch on 2008-10-23
here's a small snippet that helps you work with arrays:

[php]
<?

function displayArray($aArray) {
        if (is_array($aArray) && (count($aArray) > 0)) {
                print("<table border=1>");
                print("<tr><th>Key</th><th>Value</th></tr>");
                foreach ($aArray as $aKey => $aValue) {
                        print("<tr>");
                        if (!is_array($aValue)) {
                                if (empty($aValue)) {
                                        print("<td>$aKey</td><td><i>$aValue</i></td>");
                                } else {
                                        print("<td>$aKey</td><td>$aValue</td>");
                                }
                        } else {
                                print("<td>$aKey(array)</td><td>");
                                displayArray($aValue);
                                print("</td>");
                        }
                        print("</tr>");
                }
                print("</table>");
        } else {
                print("<i>empty or invalid</i>");
        }
}

?>
[/php]

Whenever you have an array that doesn't behave as you want, have it printed out and see how it's built up. I use this often when have some error in my code.

---

