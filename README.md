# Python-Codes
Python codes for various automations
import tkinter as tk
from tkinter import ttk
from tkcalendar import Calendar
import datetime

def on_date_selected():
    selected_date = cal.get_date()
    print(f"Selected date: {selected_date}")
    if selected_date == datetime.date.today().strftime("%Y-%m-%d"):
        print("Today is selected date. Continuing with the program.")
        # Add your code to handle the selected date here
    else:
        print("Selected date is not today. Exiting the program.")
        root.destroy()

# Create the main window
root = tk.Tk()
root.title("Created by: robin.a.gupta")

# Create a calendar widget
cal = Calendar(root, selectmode="day", date_pattern="yyyy-mm-dd")
cal.pack(pady=20)

# Create a button to get the selected date
btn_get_date = ttk.Button(root, text="Get Selected Date", command=on_date_selected)
btn_get_date.pack()

# Start the main event loop
root.mainloop()

#----------------------------------------
from easygui import *
import datetime

current_time = datetime.datetime.now()
#abc = current_time.strftime("%I:%M")
abc = current_time.strftime('%H:%M:%S')

# message to be displayed
text = "Enter time !!"

# window title
title = "Schedule Program"

# default text
#d_text = "Enter here.."
d_text = abc

# creating an enter box
output = enterbox(text, title, d_text)

print(output)  # Corrected 'print' statement

#----------------------------------------------------

import tkinter
from tkinter import filedialog
import os
import subprocess

root = tkinter.Tk()
root.withdraw()  # use to hide tkinter window

def search_for_file_path():
    currdir = os.getcwd()
    tempdir = filedialog.askopenfilename()
    if len(tempdir) > 0:
        print("You chose: %s" % tempdir)
    return tempdir


file_path_variable = search_for_file_path()

import schedule
import time

def run_vbscript():
    subprocess.Popen(["cscript", file_path_variable], shell=True)

#schedule.every().day.at("13:32").do(run_vbscript)
schedule.every().day.at(output).do(run_vbscript)

while True:
    schedule.run_pending()
    time.sleep(40)
