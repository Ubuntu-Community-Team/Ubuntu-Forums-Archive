---
title: "Java and MySQL Connector/J under Ubuntu"
date: 2008-08-06
forum: General Help
---

### Post by digysol on 2008-08-06
I will like to install Java SE version 1.6 and MySQL Connector/J under Ubuntu server edition 8.04 and want to know if it is possible.

I want to run a server application written in Java SE accessing a MySQL database via MySQL Connector/J.

---

### Post by kamaji792 on 2008-09-29
The quick answer is yes it can be done.

I will look out a code example I have at work.

Are you connecting to the database from a remote machine?

---

### Post by kamaji792 on 2008-09-30
OK here is the code I am using to connect to a database.
```
import java.sql.*;

public class DBDemo
{
  // The JDBC Connector Class.
  private static final String dbClassName = "com.mysql.jdbc.Driver";
  private static final String HOST = "ip_address_or_host_name";
  private static final String DATABASE = "database_name";
  private static final String USER = "user_name";
  private static final String PASSWORD = "password";

  public static void main(String[] args) throws
                             ClassNotFoundException,SQLException
  {
    System.out.println(dbClassName);
    // Class.forName(xxx) loads the jdbc classes and
    // creates a drivermanager class factory
    Class.forName(dbClassName);

    // Now try to connect
    String url = "jdbc:mysql://" + HOST + "/" + DATABASE;
    Connection c = DriverManager.getConnection( url, USER, PASSWORD );

    System.out.println("It works :)");
    c.close();
    }
}
```
Set the HOST, DATABASE, USER and PASSWORD for your system.

You also need to download the driver **jar** file.  Try this link _[http://dev.mysql.com/downloads/connector/j/5.1.html]("http://dev.mysql.com/downloads/connector/j/5.1.html")_.

Then you need to set your **CLASSPATH** environment variable to point to driver jar file.  I hope you know how to do this because I get into a cold sweat every time I do it :shock:

Hope this helps

---

### Post by tihsrah on 2009-05-26
> **kamaji792 said:**
> OK here is the code I am using to connect to a database.
```
import java.sql.*;

public class DBDemo
{
  // The JDBC Connector Class.
  private static final String dbClassName = "com.mysql.jdbc.Driver";
  private static final String HOST = "ip_address_or_host_name";
  private static final String DATABASE = "database_name";
  private static final String USER = "user_name";
  private static final String PASSWORD = "password";

  public static void main(String[] args) throws
                             ClassNotFoundException,SQLException
  {
    System.out.println(dbClassName);
    // Class.forName(xxx) loads the jdbc classes and
    // creates a drivermanager class factory
    Class.forName(dbClassName);

    // Now try to connect
    String url = "jdbc:mysql://" + HOST + "/" + DATABASE;
    Connection c = DriverManager.getConnection( url, USER, PASSWORD );

    System.out.println("It works :)");
    c.close();
    }
}
```
Set the HOST, DATABASE, USER and PASSWORD for your system.

You also need to download the driver **jar** file.  Try this link _[http://dev.mysql.com/downloads/connector/j/5.1.html]("http://dev.mysql.com/downloads/connector/j/5.1.html")_.

Then you need to set your **CLASSPATH** environment variable to point to driver jar file.  I hope you know how to do this because I get into a cold sweat every time I do it :shock:

Hope this helps

hey! im a new one to ubuntu so don't know how to set **CLASSPATH**:(
plz guide!!!!!

---

