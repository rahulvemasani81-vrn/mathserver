# Ex.05 Design a Website for Server Side Processing
# Date:
# AIM:
To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side.

# FORMULA:
P = I2R
P --> Power (in watts)
 I --> Intensity
 R --> Resistance

# DESIGN STEPS:
## Step 1:
Clone the repository from GitHub.

## Step 2:
Create Django Admin project.

## Step 3:
Create a New App under the Django Admin project.

## Step 4:
Create python programs for views and urls to perform server side processing.

## Step 5:
Create a HTML file to implement form based input and output.

## Step 6:
Publish the website in the given URL.

# PROGRAM :
math.html:
<html>
    <head>
        <title>mathapp</title>
        <style>
            body{
                background-color: #ff0000;
             }
            h1{
                background-color: pink;
            }
            form{
                background-color: rgb(38, 0, 255);
            }
             </style>
    </head>
    <body>
        <h1 align="center">CALCULATION OF POWER</h1>
        <form align="center"method="POST">
              {% csrf_token %}
            Intensity <input name="I" value="{{i}}">
            <br>
            <br>
            Resistance<input name="R" value="{{r}}">
            <br>
            <br>
            <input type="submit" value="calculate">
            <br>
            <br>
            power<input name="Power"value={{power}}>
        </form>
    </body>
</html>
views.py:
def CalculationPower(request): 
    context={} 
    context['power'] = "0" 
    context['i'] = "0" 
    context['r'] = "0" 
    if request.method == 'POST': 
        print("POST method is used")
        i = request.POST.get('I','0')
        r = request.POST.get('R','0')
        print('request=',request) 
        print('Intensity=',i) 
        print('Resistance=',r) 
        power = (int(i) *int(i))* int(r)
        context['power'] = power
        context['i'] = i
        context['r'] = r
        print('Power=',power) 
    return render(request,'mathapp/math.html',context)
    urls.py:
     from django.contrib import admin 
from django.urls import path 
from mathapp import views 
urlpatterns = [ 
    path('admin/', admin.site.urls), 
    path('CalculationPower/',views.CalculationPower,name="CalculationPower"),
    path('',views.CalculationPower,name="CalculationPower")
]

    

# SERVER SIDE PROCESSING:
<img width="852" height="539" alt="image" src="https://github.com/user-attachments/assets/af2c4d76-7c0c-4c43-a815-4082f2657358" />

# HOMEPAGE:
<img width="832" height="399" alt="image" src="https://github.com/user-attachments/assets/d4b00836-8924-46db-8ca2-53dd0965bf7d" />

# RESULT:
The program for performing server side processing is completed successfully.
