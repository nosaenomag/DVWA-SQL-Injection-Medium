## SQL Injection in DVWA (Medium Level)

## Overview

I analyzed a SQL Injection vulnerability in the Damn Vulnerable Web Application (DVWA) at the Medium security level, using Burp Suite for testing. The focus was on why partial security measures fail when secure coding practices aren’t fully followed.

## Key Findings

The Medium security level uses input escaping, but it doesn't use prepared statements.

SQL queries are built by joining strings, which exposes the logic.

Assumptions about numeric input aren't properly enforced.

SQL injection using numbers bypasses the sanitization.

## Exploitation Summary

I found a user-controlled id parameter through HTTP interception using Burp Suite.

String-based attacks were blocked by escaping.

I switched to manipulating numeric logic, which bypassed the filter.

I confirmed the vulnerability when I got back unauthorized records.

Here’s a screenshot showing the exploitation of the SQL injection vulnerability in DVWA:

![Exploitation Screenshot](dvwa_sql_injection_exploitation.png)

## Root Cause

Untrusted user input is directly added into SQL queries. Escaping is used, but SQL code and data aren’t separated properly.

## Proper Fix

Use prepared statements or parameterized queries.

Enforce strict validation on input.

Ensure least-privilege access to the database.

## Disclaimer

This project was done only in a controlled lab environment (DVWA) for educational purposes. No real-world systems were tested. Only use these techniques with explicit authorization.

## Author
Nosa Godwin Enoma

Linkedin: https://www.linkedin.com/in/nosa-godwin-enoma-4b6b31287/

GitHub: https://github.com/nosaenomag

