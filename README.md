# Ex.05 Design a Website for Server Side Processing
## Date:04-10-2025

## AIM:
 To design a website to calculate the body mass index (BMI) in the server side. 


## FORMULA:
BMI = W/H<sup>2</sup>
<br> BMI --> Body Mass Index
<br> W --> weight
<br> H --> Height

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
```
math.html
<html>
    <head>
    <title>BODY MASS INDEX</title>
    <style>
        body{
            background-color:yellow;
        }
        .form{
            width: 400px;
            margin: 250px auto;
            background-color:orange;
            color:blue;
            padding: 10px 20px 20px 20px;
            font-size: 20px;
        }
        .form h2{
            color:orange;
            text-align: center;
        }
        .form h3{
            color:violet
            font-size:larger;
            text-align:center
        }
        .form label{
            display:flex
        }
        .input input{
            border: dotted; 
            margin:auto;
            font-size:medium;
            width: 100%;

        }
        .h{
            text-align: center;
            padding: auto;
            margin-top: 20px;
            margin-bottom: 20px;
        }
        button{
            padding: 20px;
            background-color:red;
        }
    </style>
    </head>
<body>
    <div class="form">
        <h2><b>BMI Calculator</b></h2>
        <h3>SAMYUKTHA S (25017544)</h3>
        <form method="post">
        {% csrf_token %}
        <div class="input">
            <label for="Weight">Weight (kg):</label>
            <input type="number" name="weight" required value="{{weight}}">
        </div>
        <div class="input">
            <label for="Height">Height  (cm):</label>
            <input type="number" name="height" required value="{{height}}">
        </div>
        <div class="h">
            <button type="submit"><b>Evaluate BMI value</b></button>
        </div>
        </form>
        {% if bmi %}
        <div class="input">
            <label for="bmi">value of body mass index: </label>
            <input type="text" required value="{{bmi}}">
        </div>
        {% endif %}
    </div>
</body>
</html>
views.py
from django.shortcuts import render
def calculate_bmi(request):
    bmi=None
    catagory=None
    height=None
    weight=None
    if request.method=="POST":
        height=float(request.POST.get("height"))
        weight=float(request.POST.get("weight"))
        bmi=weight/((height/100)**2)
        print(f"Weight: {weight}kg \nHeight: {height}cm \nBMI: {bmi}")
    return render(request, "formulaapp/math.html",{"bmi": bmi, "height": height, "weight": weight})

# Create your views here.
urls.py
from django.contrib import admin
from django.urls import path
from formulaapp import views
urlpatterns = [
    path('admin/', admin.site.urls),
    path('',views.calculate_bmi,name='calculate_bmi'),

]


```

## SERVER SIDE PROCESSING:
![alt text](<samyuktha/formulaapp/Screenshot (51).png>)



## HOMEPAGE:
![alt text](<samyuktha/formulaapp/Screenshot (50).png>)



## RESULT:
The program for performing server side processing is completed successfully.
