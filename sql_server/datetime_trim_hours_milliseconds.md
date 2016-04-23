#Trim or zero-out a portion of a datetime....


To trim off the milliseconds.... (this was necessary when sending to XML for consumption by Excel...)

    DATEADD(ms, -DATEPART(ms, [date]), [date])
    
To trim off the time portion.... 
    
    DATEADD(ms, -DATEPART(dd, [date]), [date])
    

A function to do it for you....    
    
    CREATE FUNCTION dbo.JustDate(@date DATETIME)  
    RETURNS DATETIME  
    AS  
    BEGIN  
          RETURN DATEADD(dd, 0, DATEDIFF(dd, 0, @date))  
    END    